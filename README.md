# How to Host a Professional Resume Using Pelican and GitHub Pages

## Statement of Purpose
This is a simple guide on how to create, format, and host a professional resume website using modern technical writing tools. By following these instructions, you will learn to apply principles from Andrew Etter’s *Modern Technical Writing*, specifically the use of lightweight markup languages, distributed version control, and static site generators. This guide assumes basic command line knowledge but no prior experience with these tools. This guide is for anyone of any skill level interested in hosting static sites.

## Prerequisites
To complete this tutorial, you need the following:
*   **Python (3.6+):** Required to run the Pelican static site generator.
*   **Git:** A distributed version control system for tracking changes.
*   **Text Editor:** Any code editor (e.g., VS Code, Notepad++) to write content.
*   **GitHub Account:** To host your source code and website.
*   **Command Line Interface:** Terminal or PowerShell.

---

## Instructions

### 1. Install the Pelican Static Site Generator
**Action:** Open your command line and run the following command to install Pelican and Markdown:
```bash
pip install pelican markdown
```
**Context & Principle:**
Etter advocates for the principle: **"Make Static Websites"** because they are faster, more secure, and easier to host than dynamic systems like WordPress. Unlike dynamic sites requiring databases, Pelican pre-builds your content into standard HTML files. This keeps your writing separate from the server (the computer that hosts your site). By using Pelican, you focus on writing rather than server maintenance.

### 2. Create a Directory for Your Project
**Action:** Create a folder named `my-resume` and navigate into it:
```bash
mkdir my-resume
cd my-resume
```

### 3. Initialize the Project Structure
**Action:** Run the quickstart command:
```bash
pelican-quickstart
```
**Context & Principle:**
Etter emphasizes **"structure"**. `pelican-quickstart` initializes your project with standard configuration files like `pelicanconf.py`. This aligns with "treating documentation like code." Just as developers use frameworks, technical writers use structured projects. This ensures anyone viewing your project understands where content (`content/`) and settings live, making it maintainable.

### 4. Draft Your Resume Using Markdown
**Action:** Create `resume.md` inside `content/pages` and write your resume using Markdown:
```markdown
Title: Resume
Date: 2026-02-18

# Marvin McLaren
## Experience
*   Finance Manager...
```
**Context & Principle:**
This applies Etter's principle to **"Use Lightweight Markup"**. Binary formats like `.docx` are inefficient for documentation. Markdown is human-readable text that converts easily to HTML. It is future-proof and "diff-able" in version control, allowing you to track line-by-line changes. You strip away formatting distractions to focus on substance, while Pelican handles the styling.

### 5. Initialize a Git Repository (folder)
**Action:** Initialize a Git repository to track your changes:
```bash
git init
```
**Context & Principle:**
Etter's principle to **"Use Distributed Version Control"** is critical. Git creates a rigorous history of your work, allowing you to save "snapshots" (commits). If you make a mistake, you can revert instantly. Unlike "Track Changes," Git facilitates safe experimentation and collaboration without overwriting files.

### 6. Commit Your Changes
**Action:** Save your progress to the repository history:
```bash
git add .
git commit -m "Initial commit of resume source code"
```
**Context & Principle:**
This fulfills Etter's principle **"Catalogue the Diff"**. "Committing" saves a meaningful milestone. By writing a clear message, you document the *history* of your document.

### 7. Create a Repository on GitHub
**Action:**  Create a new public repository named `resume` on GitHub.com.
**Context & Principle:**
This involves using a **"Forge"** (a website that hosts code). Etter explains forges are the social hubs of development. Hosting your project on a forge makes it accessible, secure, and open for collaboration, moving your resume from a local file to a web project.

### 8. Link Your Local Folder to GitHub
**Action:** Link your local folder to GitHub (replace `USERNAME` with yours):
```bash
git remote add origin https://github.com/USERNAME/resume.git
```
**Context & Principle:**
Relates to Etter's principle **"Use Distributed Version Control"**. Pushing allows others to pull and collaborate on your code seamlessly.

### 9. Create a Branch in Your Repository
**Action:** Run the following command in your terminal:
```bash
git branch -M main
```

### 10. Push Your Code to the Forge
**Action:** Run the following command in your terminal:
```bash
git push -u origin main
```

### 11. Update publishconf.py in the Root Directory
**Action:** Set the constant SITEURL to the deployment url in publishconf.py:
```bash
SITEURL = 'https://USERNAME.github.io/resume/' 
```

### 12. Build Your Static Website
**Action:** Generate HTML files from your Markdown source:
```bash
pelican content -s publishconf.py
```
### 13. Install GitHub Pages Command-Line Interface Tool
**Action:** Run the following command in your terminal:
```bash
pip install ghp-import
```

### 14. Publish to GitHub Pages
**Action:** Use `ghp-import` to push the `output` folder to the `gh-pages` branch:
```bash
ghp-import output -b gh-pages -p
```
**Context & Principle:**
This fulfills the principle **"Publish Frequently"**. You use ghp-import to push content to the web quickly. Etter argues that publishing should not be a special event or a challenge. If it takes more than a minute to verify that content is ready for production, the process is broken.

This step also fulfills Etter's principle **"Rsync"**. While the instructions use ghp-import specifically for GitHub, Etter talks about using tools that only upload files that are updated.

### 15. View the Deployed Site
**Action:** Open a browser and type:
```
https://USERNAME.github.io/resume/
```
**Context & Principle:**
This fulfills the principle to **"Build a Website"**. You are placing your static HTML files on a public server. GitHub Pages serves these for free, giving you a professional, high-performance site without the cost of proprietary hosting. This aligns with Etter’s advice that you "should build and host a website, not distribute PDFs" because PDFs become stale immediately, whereas a website allows you to "fix inaccuracies almost instantly."


---



## Further Resources
1.  **[Markdown Tutorial - Basic Syntax](https://commonmark.org/help/tutorial/)**: A comprehensive, third-party tutorial on Markdown syntax.
2.  **[Pelican Documentation](https://docs.getpelican.com/en/latest/)**: Official docs for advanced Pelican configuration.
3.  **[GitHub Pages Documentation](https://docs.github.com/en/pages)**: Guide to hosting websites on GitHub.
4.  **[Pro Git Book](https://git-scm.com/book/en/v2)**: In-depth book about Git version control.

---

## Frequently Asked Questions (FAQ)

### Q: Why is Markdown better than raw HTML?
**A:** Markdown is designed to be readable as-is. HTML is cluttered with tags (like `<div>`) that make reading difficult. As Etter explains, "Lightweight markup... is human-readable in raw form," allowing you to focus on content, not syntax.

### Q: Why don't I see changes when I refresh the website?
**A:** When you edit `resume.md`, you only change the *source*. You must run `pelican content` to regenerate the HTML files in `output/`. The website displays `output/`, so every source change requires a rebuild.

---

## Credits
This guide was produced for Computer Science 2600.
*   **Author:** Ji Min Ryu, 7939825
*   **Peer Review Group:** Jade Lee, Harkeet Bal
*   **References:**
    *   Etter, Andrew. *Modern Technical Writing*. 2016.
    *   Pfeiffer, William S. *Technical Communication*.
