# (APPENDIX) Appendix

# Version control with GitHub

>Excuse me, do you have a moment to talk about version control?^[https://peerj.com/preprints/3159v2/]

There is a lot to say about GitHub and why one may use it. An extensive discussion on this topic and basically everything you will learn in this chapter can be found in [Happy Git and GitHub for the useR](https://happygitwithr.com/big-picture.html).

This chapter will introduce the basics on how to collaborate with other people using GitHub, which is probably the reason why you are reading this in the first place. 


## Headstart into Git and GitHub with RStudio

The following post provides a quick introduction on how to set up Git and GitHub and connect your GitHub account with RStudio: https://www.bioinformatics.babraham.ac.uk/training/RStudio_GitHub/Initial_setup.html.

Once this is done, you should be able to connect and download online GitHub repositories and are able to start collaborating on projects immediately.



## Basic GitHub routine


Open your Git terminal in R and start with these lines of code.


Add files:


```bash
git add .
```

Commit changes: 


```bash
git commit -m "Add important changes"
```

Push your commits:


```bash
git push
```
...


## Common problems

The following should provide a summary of common problems encountered when using Git. It also serves as a reminder for myself.

### Too large files


Original post of the answer: https://stackoverflow.com/a/17890278.

1. Download the BFG Repo-Cleaner jar file "bfg-x.xx.x.jar" (e.g. "bfg-1.14.0.jar") from https://rtyley.github.io/bfg-repo-cleaner/.

2. Place the file in the directory of your R project, the same of the .git folder.

3. Open the terminal in this folder (e.g. via RStudio > Git > Shell...)

4. Type in the terminal:


```bash
java -jar bfg.jar --strip-blobs-bigger-than 100M
```

The file name "bfg.jar" must match the name of your jar file and the file size limit can be changed (e.g. 50M for 50 )

5. If you do not encouter an error, type:


```bash
git gc --prune=now --aggressive
```

to clean the dead data.


If you encounter the following error `Warning : no large blobs matching criteria found in packfiles - does the repo need to be packed?`, refer to this post https://stackoverflow.com/q/61769785 and type `git gc` prior to step 4.


### .gitignore does not instantly work

Just do:

```bash
git rm -r --cached .
git add .
git commit -m "Drop files from .gitignore"
```



