# Building and Hosting My Resume with Pelican and GitHub

## Statement of Purpose
This README documents how I converted my resume to **Markdown**, generated a **static website** using **Pelican**, and **hosted** it on **GitHub**. It is intended for Marvin McLaren (and anyone at a similar level of technical familiarity) who wants to see a straightforward application of **Andrew Etter’s** principles from *Modern Technical Writing*. I also draw on guidelines from William S. Pfeiffer’s *Technical Communication* to ensure the instructions are clear, concise, and properly structured.

---

## Prerequisites
Before you begin, you will need:

1. **A Markdown-capable Text Editor**  
   - Tools like Visual Studio Code, Sublime Text, or Atom work well.  
   - Andrew Etter recommends using a *lightweight markup language* like Markdown for documentation clarity and version control.

2. **GitHub Account**  
   - [https://github.com/](https://github.com/) (free sign-up)  
   - This is where you’ll host both the project source and the final rendered site (via GitHub Pages or a branch approach).

3. **Git**  
   - A version control system for creating local repos and pushing code to GitHub.  
   - Confirm with `git --version`.

4. **Python 3**  
   - Required to run Pelican.  
   - Check by typing `python3 --version` or `python --version` in your terminal.

5. **Pelican (with Markdown Support)**  
   - Install via:
     ```bash
     python3 -m pip install "pelican[markdown]"
     ```
   - This will process `.md` files into static HTML.

6. **A Resume in Markdown**  
   - If you only have a PDF or Word resume, copy the text into a `.md` file (e.g., `resume.md`).  
   - Use headings, lists, and bold text to reflect your sections (Skills, Experience, Education, etc.).

> **(Pfeiffer Guideline #1: Select the correct technical level)**  
> These instructions assume basic familiarity with the command line and Markdown, but no deep expertise in software development or DevOps is required.

---

## Instructions

Below is a detailed, **step-by-step** guide on how I built and published my resume site, referencing Andrew Etter’s recommendations for modern technical documentation.

### 1. Convert or Create Your Resume in Markdown
- **Etter Principle**: *Opt for a lightweight markup language*  
  In *Modern Technical Writing*, Etter emphasizes that Markdown is easier to read, merge, and maintain than proprietary file formats or heavy markup languages.

- **Practical Steps**:
  1. **Create** a file called `resume.md` using your text editor.  
  2. **Use** headers (`#`, `##`, `###`) to structure your content (e.g., “Skills,” “Work History,” “Education”).  
  3. **Incorporate** bullet points for job responsibilities, short achievements, or skill listings.  
  4. **Add** a short metadata block at the top for Pelican:
     ```markdown
     Title: Resume
     Date: 2025-03-05
     Category: Personal
     ```
     This helps Pelican treat the file as a valid content article/page.

### 2. Initialize a Pelican Project
- **Etter Principle**: *Use a static site generator instead of a full CMS*  
  This results in a **lighter, faster, and more secure** website with less overhead.

- **Practical Steps**:
  1. **Make** a new directory, for instance `website/`, and open it in a terminal.  
  2. **Run**:
     ```bash
     pelican-quickstart
     ```
     - Provide a site title (e.g., “My Resume Site”), author name, and time zone when prompted.  
  3. **Check** that Pelican created files like `pelicanconf.py`, `publishconf.py`, and folders named `content/` and `output/`.

### 3. Place `resume.md` in the `content` Folder
- **Etter Principle**: *Organize docs in a single source location*  
  Placing your `.md` in `content/` aligns with Pelican’s default structure and clarifies where the source text resides.

- **Practical Steps**:
  1. **Move** `resume.md` into the `content/` folder.  
  2. **Verify** the top lines match the Pelican front matter format (“Title: …”).  
  3. **Ensure** your headings and bullet points render well in a Markdown preview if you want a quick check.

> **(Pfeiffer Guideline #5: Place only one action in each step)**  
> Each bullet is short and starts with a verb—ensuring clarity and preventing confusion.

### 4. Generate and Preview the Website Locally
- **Etter Principle**: *Test often to find and fix issues quickly*  
  Etter advocates frequent iterations—especially with static site builds that are fast to regenerate.

- **Practical Steps**:
  1. **Open** a terminal in your project folder (the one containing `pelicanconf.py`).  
  2. **Run**:
     ```bash
     pelican content
     ```
     This reads `.md` files in `content/` and outputs `.html` into `output/`.  
  3. **Preview** by typing:
     ```bash
     pelican --listen
     ```
     Then visit [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser to see your site.  
  4. **Check** that your resume appears properly. If needed, revise `resume.md` and rebuild.

### 5. Set Up Git Version Control
- **Etter Principle**: *Use distributed version control to track changes and collaborate*  
  Keeping your Pelican project in Git ensures your entire site is easily managed, revertible, and shareable.

- **Practical Steps**:
  1. **Initialize** Git:
     ```bash
     git init
     git add .
     git commit -m "Initial commit with Pelican resume"
     ```
  2. **Create** a new repository on GitHub (e.g., “Comp-2600-A2”) and copy its URL.  
  3. **Add** the remote and push:
     ```bash
     git remote add origin https://github.com/YourUsername/Comp-2600-A2.git
     git push -u origin main
     ```
     *(Use personal access tokens or SSH keys instead of your password.)*

### 6. Publish the Static Site on GitHub
- **Etter Principle**: *Make documentation publicly accessible on a forge*  
  Etter suggests using a popular forge (like GitHub) so external collaborators or viewers can easily read or contribute.

**Common Approaches**:

#### A) Host in a `docs/` Folder on Main Branch
1. **Build** again:
   ```bash
   pelican content