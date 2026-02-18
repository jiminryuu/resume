# How to Host a Professional Resume Using Pelican and GitHub Pages

## Statement of Purpose
This is a simple guide on how to create, format, and host a professional resume website using modern technical writing tools. By following these instructions, you will learn to apply principles from Andrew Etter’s *Modern Technical Writing*, specifically the use of lightweight markup languages, distributed version control, and static site generators. This guide assumes basic command line knowledge but no prior experience with these tools. This guide is for anyone of any skill level, interested in hosting static sites.

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
Etter advocates for the principle to **"Make Static Websites"** (Ch 3) because they are faster, more secure, and easier to host than dynamic systems like WordPress. Unlike dynamic sites requiring databases, Pelican pre-builds your content into standard HTML files. This workflow separates content from complex infrastructure, ensuring your resume loads instantly and remains secure. By using Pelican, you focus on writing rather than server maintenance.

### 2. Create a Directory for Your Project
**Action:** Create a folder named `my-resume` and navigate into it:
```bash
mkdir my-resume
cd my-resume
```
**Context & Principle:**
Organization is key. By creating a dedicated directory, you establish a clean workspace for your "source tree." In static site generation, your project folder contains the "source" (content and config), while a separate `output` folder contains the "built" website. You write the source to generate the site.

### 3. Initialize the Project Structure
**Action:** Run the quickstart command:
```bash
pelican-quickstart
```
**Context & Principle:**
Etter emphasizes **automation and structure**. `pelican-quickstart` scaffolds your project with standard configuration files like `pelicanconf.py`. This aligns with "treating documentation like code." Just as developers use frameworks, technical writers use structured projects. This ensures anyone viewing your project understands where content (`content/`) and settings live, making it maintainable.

### 4. Draft Your Resume Using Markdown
**Action:** Create `resume.md` inside `content\pages` and write your resume using Markdown:
```markdown
Title: Resume
Date: 2026-02-18

# Marvin McLaren
## Experience
*   Finance Manager...
```
**Context & Principle:**
This applies Etter's principle to **"Use Lightweight Markup"** (Ch 3). Binary formats like `.docx` are inefficient for documentation. Markdown is human-readable text that converts easily to HTML. It is future-proof and "diff-able" in version control, allowing you to track line-by-line changes. You strip away formatting distractions to focus on substance, while Pelican handles the styling.

### 5. Initialize a Git Repository
**Action:** Initialize a Git repository to track your changes:
```bash
git init
```
**Context & Principle:**
Etter's principle to **"Use Distributed Version Control"** (Ch 3) is critical. Git creates a rigorous history of your work, allowing you to save "snapshots" (commits). If you make a mistake, you can revert instantly. Unlike "Track Changes," Git facilitates safe experimentation and collaboration without overwriting files.

### 6. Commit Your Changes
**Action:** Save your progress to the repository history:
```bash
git add .
git commit -m "Initial commit of resume source code"
```
**Context & Principle:**
"Committing" saves a meaningful milestone. By writing a clear message, you document the *history* of your document. This transforms writing from a linear stream into a managed lifecycle where every update is recorded.

### 7. Create a Repository on GitHub
**Action:**  Create a new public repository named `resume` on GitHub.com:
**Context & Principle:**
This involves using a **"Forge"**. Etter explains forges are the social hubs of development. Hosting your project on a forge makes it accessible, secure, and open for collaboration, moving your resume from a local file to a web project.

### 8. Push Your Code to the Forge
**Action:** Link your local folder to GitHub and upload your code (replace `USERNAME` with yours):
```bash
git remote add origin https://github.com/USERNAME/resume.git
git branch -M main
git push -u origin main
```
**Context & Principle:**
Pushing publishes your *source* code. This transparency aligns with the open-source culture Etter advocates, allowing others to see your build structure and learn from it.

### 9. Update publishconf.py file
**Action:** Set constant SITEURL to deployment URL in publishconf.py:
```bash
SITEURL = 'https://USERNAME.github.io/resume/' 
```

### 10. Build Your Static Website
**Action:** Generate HTML files from your Markdown source:
```bash
pelican content -s publishconf.py
```
**Context & Principle:**
This is the "compilation" step. Your Markdown is "built" into a website, aligning with Etter's view of documentation as a product of a build system. `pelican` applies a theme to your text, producing professional HTML in `output/`. This separation allows you to change the site's look by switching themes without touching the content.

### 11. Publish to GitHub Pages
**Action:** Use `ghp-import` to push the `output` folder to the `gh-pages` branch:
```bash
pip install ghp-import
ghp-import output -b gh-pages -p
```
**Context & Principle:**
This fulfills the principle to **"Build a Website"**. You are placing your static HTML files on a public server. GitHub Pages serves these for free, giving you a professional, high-performance site without the cost of proprietary hosting.

### 12. View deployed site
**Action:** Open browser and type:
```
https://USERNAME.github.io/resume/
```
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
*   **Author:** Ji Min Ryu 7939825
*   **Peer Review Group:** Jade Lee, Harkeet Bal
*   **References:**
    *   Etter, Andrew. *Modern Technical Writing*. 2016.
    *   Pfeiffer, William S. *Technical Communication*.
