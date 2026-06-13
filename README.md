# Lithic-Puzzle

To find the hidden challenge, I initially used the "Inspect" function within Chrome and spent some time doing basic Ctrl+F searches through the HTML, looking for obvious strings in the console.

After a few minutes, I pasted the HTML block into Gemini AI just to see if it spotted anything anomalous. Honestly, I was actually pretty bummed by what happened next. The AI immediately identified the "problem-solving" link, decoded it, and explained the entire cipher to me before I even had a chance to dig into it myself. It completely spoiled the fun of cracking the puzzle manually, but it definitely proved how efficiently AI can shortcut this kind of log-diving. I'd be lying if I said I haven't used AI in the exact same ways in the past - digging through a mass of complex code or log files.

It explained that this string of garbage tied to the "problem-solving" link is a Base64 encoded text block that when decoded translates into a hidden set of instructions and a Python script.
It also explained the script uses a basic XOR cipher to decrypt a password, checks my environment variables, and generates a unique SHA-256 hash based on my name.

From PowerShell, I ran:
 $env:DONT_PANIC="1"; python puzzle.py --candidate "Jeffrey Baffi"  
 
The exact output I received was: 
Decrypted password: 42
Candidate: Jeffrey Baffi
Proof code: 11ad49672e91
