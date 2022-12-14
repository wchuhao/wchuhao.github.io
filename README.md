# Static Websites And GitHub Pages

This project is a demonstration of how to use the static website generator Jekyll with GitHub Pages

## Purpose
Explain how to host a resume on GitHub Pages. Also, introduce and demonstrate the principles of Andrew Etter's book Modern Technical Writing
## Getting Started

## Prerequisites

Requirements for the software and tools used in this guide. 
- [GitHub Account](https://github.com/join)
- [Git](https://git-scm.com/downloads)
- [Ruby ( If you are on Windows the installer is recommended)](https://www.ruby-lang.org/en/downloads/)
- [Jekyll](https://jekyllrb.com/docs/installation/)
- A Markdown Resume. (See More Resource for Markdown Tutorial)
## Instructions
### Step 1: Creating a GitHub Repository

1. Start the creation of a repository by selecting the outlined button in the image below 
![image](/img/step1.png)
2. Enter the required information of your repository. (Ignore the warning I have for the Repository name)
    - Enter repository name as "username.github.io" where username is you github username
    - Set visibility to public
    - Select option to initialize repository with a README
    - Click **Create repository**
![image](/img/createmenu.png)
3. In the newly created repository navigate to **Settings**
![image](/img/settings.png)
4. In the sidebar click **Pages**
5. Set the deployment source to *Deploy from a branch* under the **Source** section
6. Set the desired publishing branch under the **Branch** section
    - To keep it simple it is recommended that the main branch and root directory is the publishing branch
![image](/img/pagesSetting.png)
7. Click Save
## Step 2: Setting up Jeykell for your repository

1. Click on the **Code** tab of your repository
2. Click on the green **Code** button
3. Copy the URL for your repository
![image](/img/clone.png)
4. Open the command prompt by searching "Command Prompt" in your OS search function
5. Create a new directory on your computer for your local repository
6. Navigate to the new directory where you want to clone the repository to by running the following command
```
cd path/to/your/directory
```
7. Run the follow command. Besure to replace {YOUR GITHUB REPO URL} with the URL copied in step 2.3
```
git clone {YOUR GITHUB REPO URL}
```
8. Navigate into the newly cloned repository by running
```
cd path/to/your/repository 
```
9. Run ```jekyll new --skip-bundle .```
    - You may need to run the command as the follow if there are conflicts
    ```
    jekyll new --skip-bundle --force .
    ```
10. Open the Gemfile created by Jekyll
11. Comment out the line that starts with ```gem ???jekyll??? ```with #
12. Replace the comment the ```# gem "github-pages"``` with ```gem "github-pages", "~> 227", group: :jekyll_plugins```
13. Save the Gemfile
14. Run ```bundle install``` from the command prompt
15. Open the file _config.yml 
16. Add changes by running the following in the command prompt
```
git add . 
``` 
17. Commit changes to the remote repository by running the follow command in the command prompt
```
git commit -m "Initial GitHub pages site with Jekyll"
```
18. Push your changes to the remote repository with the following command replacing BRANCH with your branch name
```
git push -u origin BRANCH 
```
- Note: You may be prompted to authorize the action, you can do so by following the steps in the prompt.

### Step 3: Adding your resume

1. Add your resume to the directory you had set for publishing in Step 1.6 in the local repository you cloned
2. Run ```git add . ``` 
2. Run ```git commit -m "adding resume"``` 
3. Run ```git push -u origin BRANCH ```

### Step 4: Changing the Theme
- If you don't want to change the theme leave everything as is. **This tutorial assume the theme is the default one, Minima**
1. Open the *_config.yml* file in your local repository
2. Add the following, replace ```REMOTE/THEME/LOCATION``` to the location of one of the [supported themes](https://pages.github.com/themes/)
    - NOTE: For more information as to what to place in the ```remote_theme``` parameter see the README in the theme's repository 
    - NOTE: Use ```theme: THEME_NAME``` instead of ```remote_theme: REMOTE/THEME/LOCATION```if the theme is not remote.

```
remote_theme: REMOTE/THEME/LOCATION
plugins:
  - jekyll-remote-theme
  - jekyll-feed
```
3. Run ```git add . ``` 
4. Run ```git commit -m "Changing theme"``` 
6. Run ```git push -u origin BRANCH ```

### Step 5: Setting your resume as the default home page
1. Open the directory for your local repository
2. rename your resume to `index.md`
3. Delete the **_post** folder as we will not need it 
4. Run ```git add . ``` 
5. Run ```git commit -m "Setting resume as default home page"``` 
6. Run ```git push -u origin BRANCH ``` again replacing BRANCH with your branch name

## Step 6: View Your Static Page 
1. Navigate to the settings tab of your repository
2. Click on Pages on the sidebar
3. Click visit site
![Image](/img/visit.png)
4. You should see something similar to the following
![Alt Text](/gifs/resume.gif)

## Relation Between Etter's Concepts and Steps to Hosting a Static Site

By following the steps above, you have just completed many of Etter's concepts and practices of modern technical writing. Let's examine how the core concepts relate to the steps we just took.  

1. Use a lightweight markup language

    - There are many benefits to using a markup language. First, it is human-readable, thus making it easier for almost anyone to contribute. In Etter's book, it is highlighted that having documentation that encourages others to contribute provides a great advantage. Etter(2016) argues that it allows you to use the knowledge of more people. Additionally, Etter(2016) claims that lightweight markup languages are more portable than What You See Is What You Get (WYSIWYG) editors. This again makes it easier for people to contribute as compatibility issues won???t block them. We can see the effects of using a lightweight markup language in **Step 4: Changing the Theme**. When doing Step 4 you might have noticed how easy it was to know what each parameter did in the _config.yml. Even without knowing yml, it is intuitive what needs to be changed to change the theme when using a lightweight markup language like yml.

2. Format a document with a static site generator

    - Etter(2016) states in their book that static sites are a simple, fast, and portable way to format your documents. Unlike full-on websites, static sites are much more lightweight. They have no database and are independent of server-side programs, as such, they are perfect for documents. In Etter???s book, the recommended way to create static websites is through a generator, such as Jekyll which we are using here. Despite us using Jekyll, Etter's book recommends Sphinx, which was built for documentation and comes with a built-in search. In Etter???s book, it is noted that the selection of a theme is important. A theme with a good interface and a search function is important to the site. We have demonstrated this concept through **Step 2** and **Step 4** where we set up a static site generator and select a theme.

3. Share/host documents on a distributed version control system

    - Distributed version control systems (DVCS) are a great way to allow for concurrent work on the same file without any headaches. Etter(2016) argues that while most DVCS are overkill for the documentation workflow, it is still important to them as most developers will use them. One of the big appeals to DVCS is that they allow documentation and code to stay in sync, and it encourages developers to contribute as well. While Git/GitHub may seem complicated, however, after setting up local, the workflow really just boils down to making changes, committing, and pushing. We demonstrated this concept in **Step 1** where we set up the remote repository, in **Step 2** where we set up the local repository and we demonstrated the workflow of changing/adding a file in **Step 3** where we uploaded the resume.

## More Resources
 - [Modern Technical Writing: An Introduction to Software Documentation](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)
 - [Markdown Tutorial](https://www.markdowntutorial.com/)
 - [Github Markdown Syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
 - [Markdown Readme Examples](https://github.com/matiassingers/awesome-readme)
 - [More about Git/GitHub](https://docs.github.com/en/get-started/using-git/about-git)

## Authors and Acknowledgements

  - [Modern Technical Writing: An Introduction to Software Documentation](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS) - Referenced for the concepts used
  - [Minima](https://github.com/jekyll/minima) - Used to style static page
  - Members of Group 14: Tanish Sood, Juan Armijos, Khush Bhrugesh Patel - Provided feedback for readme

## FAQ

**Q:** Why is Markdown better than a word processor?  
**A:** Markdown is better than a word processor because it is portable and lightweight. You can open Markdown files with any text viewer on any operating system.

**Q:** Why is my resume not showing up?  
**A:** The Resume is not showing possibly because of the file location. Ensure that the Resume is located in the root directory. This could also happen if you did not rename your resume in **Step 5** to index.md.
