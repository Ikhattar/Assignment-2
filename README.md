# Building and Hosting My Resume with Pelican and GitHub

## Statement of Purpose

##### Guideline 1: Select the correct technical level

This README explains how I converted my resume into a Markdown-based static site using Pelican and then published it on GitHub. This is for Marvin or anyone else who has basic technical knowledge and it shows best ways to work with a Markdown file and how to upload projects on GitHub. I am also trying to keep the instructions straightforward, simple, and well-structured for easier access.

***

## Prerequisites
##### Guideline 10: Keep a simple style
Before you begin, you will need:

1. **A Markdown-capable Text Editor**  
   * Tools like [VS Code](https://code.visualstudio.com/download), [Sublime Text](https://www.sublimetext.com/download) or even [R Studio](https://posit.co/download/rstudio-desktop/). 

   * For this I used VS code. 

2. **GitHub Account**  
   * A [GitHub](https://github.com/) account is necessary.
   * This is where you’ll host both the project source and the final rendered site.

3. **Git**  
   * A version control system for creating local repos and pushing code to GitHub.  
   * Confirmation of git can be done by running this command `git --version`.

4. **Python**  
   * Python is required to run Pelican. 
   * The official download page for [Python](https://www.python.org/downloads/)
   * Check by typing `python --version` in your terminal.



5. **Pelican (with Markdown Support)**  
   * Pelican is installed by typing this in terminal
   ```
   python -m pip install "pelican[markdown]"
   ```
   * This will help to process `.md` files into static HTML.

6. **Make a Resume in Markdown**  
   * If you only have a PDF or Word resume, copy the text into a `.md` file (e.g., `resume.md`).  
   * Make headings, lists, and bold text to reflect your sections (Skills, Experience, Education, etc.).


---

## Instructions
##### Guideline 6: Lead off each action step with a verb

Below is a detailed, **step-by-step** guide on how I built and published my resume on GitHub.

### Step 1:
  * Open your resume `resume.md` 
  * Add a short metadata block at the top for Pelican:
     ```markdown
     Title: Resume
     Date: 2025-03-05
     Category: Assignment
     ```

### Step 2: Initialize a Pelican Project
 * Make a new directory, for example `website` or `Pelican Resume`, and open it in a terminal.  
 * Run this command in terminal:
  ```
  pelican-quickstart
  ```
 * Answer a few question that will be asked 
 ```
   * Where do you want to create your new web site? [.]
   *  What will be the title of this web site? Ferrets Unlimited
   *  Who will be the author of this web site? Pafnuty the Ferret
   *  What will be the default language of this web site? [en]
   *  Do you want to specify a URL prefix? e.g., https://example.com (Y/n) n
   *  Do you want to enable article pagination? (Y/n)
   *  How many articles per page do you want? [10]
   *  What is your time zone? [America/Winnipeg]
   *  Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n)
   *  Do you want to upload your website using FTP? (y/N)
   *  Do you want to upload your website using SSH? (y/N)
   *  Do you want to upload your website using Dropbox? (y/N)
   *  Do you want to upload your website using S3? (y/N)
   *  Do you want to upload your website using Rackspace Cloud Files? (y/N)
   *  Do you want to upload your website using GitHub Pages? (y/N)
   ```
 * Check that Pelican created files like `pelicanconf.py`, `publishconf.py`, and folders named `content` and `output`.

### Step 3: Place `resume.md` in the `content` Folder
  * Move `resume.md` into the `content` folder.  
  * Verify the top lines match the Pelican front matter format (“Title: …”).  
  * Ensure your headings and bullet points work well in a Markdown and preview it [here](https://markdownlivepreview.com) if you want a quick check.

### Step 4:  Generate and Preview the Website Locally
   * **Open** a terminal in your project folder (the one containing `pelicanconf.py` and other files).  
   * Run this in terminal:
     ```
     pelican content
     ```
     This reads `.md` files in `content` and outputs `.html` into `output`.  

   * Preview by typing:
     ```
     pelican --listen
     ``` 
   * Then visit [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser to see your site.  
   * Check that your resume appears properly. If needed, revise `resume.md` and rebuild.

### Step 5: Set Up GitHub Repository

   * Setup a GitHub Repository by going to [ GitHub Dashboard](https://github.com/dashboard) and clicking new repository.
   * Create a new repository on GitHub (e.g., “example”) and copy its `URL` from GitHub.  
   * Select `settings` in Repository and then select `pages`
   * Select `gh-pages` in branch and then `/root` and save it

### Step 6: Changing `publishconf.py`
   * Open terminal and enter these commands with `URL` from Step 5 (You can also copy from GitHub after you make Repository):
     ```
     git remote add origin URL
     git branch -M main
     git push -u origin main
     ```
   * Copy the `URL` from GitHub and open `publishconf.py`
   * Enter the `URL` in
   ```
    SITEURL = "URL"
   ```

### Step 7: Publish the Static Site on GitHub
##### Guideline 5: Place only one action in each step

 * Enter these command in your terminal 
 ```
 pelican content -s publishconf.py   
 ```
 ```
 ghp-import output -b gh-pages
 ```
 ```
 git push origin gh-pages
 ```

---

## Further Resources / Readings

1. [Get Pelican](https://docs.getpelican.com/)  
   *A guide on how to use Pelican*

2. [GitHub Pages](https://docs.github.com/en/pages)  
   *Step-by-step instructions on how to start GitHub Repositories and also get help or troubleshoot*

3. [Markdown Preview](https://markdownlivepreview.com)  
   *Preview Markdown files as you write.*

4.  [Python](https://www.python.org/)  
   *Downloads Python, which is needed by Pelican.*
5. [Markdown Tutorial](https://www.markdowntutorial.com/)
   *To learn features for Markdown*
---
## A FAQ
 * ##### Why is Markdown better than writing raw HTML? 
  Markdown is simpler and more readable than raw HTML, which is easier to edit in future. Markdown has alot of features like '#' for headings '-' or '*' for bullets making it easier to read and edit.

 * ##### I changed the Markdown version of my resume, so why don’t I see the changes when I refresh the website in my browser?
  Everytime you change your resume you have to type this in your terminal 
 `pelican content` and then in your terminal again type the command below to check if your resume is correct `pelican --listen` now you will have to repeat Step 7 again. Enter these command in your terminal `pelican content -s publishconf.py` `ghp-import output -b gh-pages` `git push origin gh-pages` This will update the resume online


---

## Credits
 * Author: Ish Khattar  
 * Peer Editors: Davud Habibullah
 * Third-Party Materials:
   * [Pelican](https://docs.getpelican.com/) – a static site publishing tool All rights reserved.
   * [Markdown Tutorial](https://www.markdowntutorial.com/) - To learn features for Markdown
   * [Markdown Preview](https://markdownlivepreview.com) - Preview Markdown files as you write.
   * [Python](https://www.python.org/) - Download Python and use it for Pelican
   * [GitHub](https://docs.github.com/en/pages) - To upload the project
   * Andrew Etter’s *Modern Technical Writing*
