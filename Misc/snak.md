# snak
> Snake has gone turn-based, but the game takes too long...

## Solution


Automate the game with Powershell 7. The game runs until the score reaches 100.

```powershell


# Function to read raw bytes and convert to string
function Get-oanRawBytes {
    param (
        [int]$bufferSize = 4096  # Use a larger buffer size for efficiency
    )
    $stringBuilder = New-Object System.Text.StringBuilder
    $buffer = New-Object byte[] $bufferSize
    $startTime = [System.Diagnostics.Stopwatch]::StartNew()

    while ($true) {
        while ($stream.DataAvailable) {
            $bytesRead = $stream.Read($buffer, 0, $bufferSize)
            if ($bytesRead -gt 0) {
                $stringBuilder.Append([System.Text.Encoding]::UTF8.GetString($buffer, 0, $bytesRead)) | Out-Null
            }
        }

        if ($stringBuilder.ToString().EndsWith("): ") -or $startTime.ElapsedMilliseconds -ge 500) {
            break
        }

        Start-Sleep -Milliseconds 2 # Small sleep to prevent tight loop
    }

    $allData = $stringBuilder.ToString()
    if ($allData.Length -gt 0) {
        return $allData
    } else {
        return $null
    }
}


function Find-SnkPositions {
    param (
        $data
    )

    $lines = $data -split "`n"
    $lines = $lines | Where-Object { $_ -match "#" }

    $snake_pos_y = 0
    $snake_pos_x = 0
    $apple_pos_y = 0
    $apple_pos_x = 0
    $y = 0

    foreach ($line in $lines) {
        $y++
        if ($line -match 'o') {
            $snake_pos_y = $y
            $snake_pos_x = $line.IndexOf('o')
            #write-host -f Green "Snake position: $snake_pos_x, $snake_pos_y"
        }
        
        if ($line -match 'g') {
            $apple_pos_y = $y
            $apple_pos_x = $line.IndexOf('g')
            #write-host -f Green "Apple position: $apple_pos_x, $apple_pos_y"
        }
    }

    return @{
        snake_pos = @($snake_pos_x, $snake_pos_y)
        apple_pos = @($apple_pos_x, $apple_pos_y)
    }
}
function Get-SnkMove {
    param (
        $pos
    )

    $snake_x = $pos.snake_pos[0]
    $snake_y = $pos.snake_pos[1]
    $apple_x = $pos.apple_pos[0]
    $apple_y = $pos.apple_pos[1]

    $horizontal = $apple_x - $snake_x
    $vertical = $snake_y - $apple_y

    return @{horizontal=$horizontal; vertical=$vertical}

}


#
# SCRIPT
#

# Define server information
$gameHOST = 'challenges.ctf.sikt.no'
$PORT = 5010

# Snake commands
$UP = "1"
$DOWN = "2"
$LEFT = "3"
$RIGHT = "4"

# Directions
$directions = @{
    "1" = "↑"
    "2" = "↓"
    "3" = "←"
    "4" = "→"
}

# Function to connect and send commands to the server
$client = New-Object System.Net.Sockets.TcpClient
$client.Connect($gameHOST, $PORT)
$stream = $client.GetStream()
$stream.ReadTimeout = 1500

$writer = New-Object System.IO.StreamWriter($stream) 
#$reader = New-Object System.IO.StreamReader($stream)

# Timing
$start = Get-Date

do {
    $data = Get-oanRawBytes
    Write-Host -f Green $data
} while ($data -notmatch "Start Game?")

Write-Host -ForegroundColor Yellow "Sending 'Y' to start the game"

$writer.WriteLine("Y")
$writer.Flush()

$gameOn = $true
$loops = 0 # Just to prevent infinite loop
Clear-Host
$cursor_position = [System.Console]::GetCursorPosition()

while ($gameOn -and ($loops -lt 10000)) {

    #Start-Sleep -Milliseconds 100
    $data = Get-oanRawBytes
    if ($data -match "##") {
        # Probably a game board
        [System.Console]::SetCursorPosition($cursor_position[0], $cursor_position[1])
        Write-Host -ForegroundColor Cyan $data

        $positions = Find-SnkPositions -data $data
        $moves = Get-SnkMove -pos $positions

        if ($moves.horizontal -gt 0) {
            $move = $RIGHT
        } elseif ($moves.horizontal -lt 0) {
            $move = $LEFT
        } elseif ($moves.vertical -gt 0) {
            $move = $UP
        } elseif ($moves.vertical -lt 0) {
            $move = $DOWN
        }

        Write-Host -f Yellow "Move: $($directions["$move"])"
        $writer.WriteLine($move)
        $writer.Flush()
        

    } else {
        $gameOn = $false
        Write-Host -BackgroundColor Red -ForegroundColor Black $data
    }

    $loops++
}

```
> Flag: SiktCTF{snak:_hiss_hiss_gratz_u_are_good_at_game!!!}