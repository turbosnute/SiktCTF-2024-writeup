# Welcome
> Welcome to SiktCTF 2024! To get started, solve this short challenge first Read the rules and find the first flag.

## Solution 
Flag is present in the source of the rules page.

```html
<ol class="spaced-list">
    <li>The flag format follows this regex pattern: /^SiktCTF{.*}$/.</li>
    <li>Here's an example of a valid flag: SiktCTF{th1s_i5_4_fl4g’+!-.@#$%?}. Any flag not in this format is considered invalid.</li>
    <li>Teams can have up to 5 members to qualify for prizes (refer to the prize details for more information).</li>
    <li>DDoS attacks are strictly forbidden.</li>
    <li>Brute-forcing any server challenge is prohibited unless explicitly allowed.</li>
    <li>Collaboration between different teams is not permitted.</li>
    <li>Hoarding flags is not allowed.</li>
    <li>The first flag is commented away on this page</li>
    <!-- SiktCTF{Welcome_To_The_CTF!_Have_Fun!} -->
    <li>All decisions made by the SiktCTF admins in case of disputes are final.</li>
</ol>
```

> Flag: SiktCTF{Welcome_To_The_CTF!_Have_Fun!}