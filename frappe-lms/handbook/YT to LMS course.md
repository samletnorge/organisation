
Format: Role-Task-Context
Tools: [yt playlist extractor](https://youtube-playlist-link-extractor.vercel.app/)

### The "LMS Architect" Prompt
> **Act as an LMS Specialist. I will provide a list of YouTube titles and URLs. Map them into a CSV format with the following headers: [Paste your headers here]. 
> 
> Use these constraints:
> 1. Status: "Approved", Color: "Gray", Evaluator: "jane.smith@example.com".
> 2. Generate a professional 1-sentence description for each video based on its title.
> 3. Map all videos to Chapter: "usage" and Course: "Getting started with Notion Projects".
> 4. Ensure no columns are empty. Use "Software" as the default category.**

***

### Why this works:
1.  **Header Mapping:** By providing the headers, you ensure the AI doesn't guess your LMS's specific database structure.
2.  **Hardcoded Values:** Specifying "Gray," "Approved," and the email prevents the "Invalid Value" errors you encountered earlier.
3.  **Creative Automation:** Asking the AI to "generate a 1-sentence description" saves you from having to watch every video to write metadata.
4.  **Error Prevention:** The instruction "Ensure no columns are empty" forces the AI to fill in placeholders rather than leaving commas blank.

### Pro-Tip for Playlists:
If the playlist is long, you can use a browser extension (like "YouTube Summary with ChatGPT") to copy the entire transcript or list of titles in one click, then paste that text directly below the prompt above.


