# Setup guide for installing R, RStudio, and GitHub

## Install R

1. Open http://cran.rstudio.com/ , click the "Download R for Windows" link and then the "base" link
2. Download the R for Windows installer
3. Run the installer

## Install RStudio

1. Open http://www.rstudio.com/products/rstudio/download/
2. Download the Windows XP installer
3. Run the installer

	
## Install git

1. Open https://windows.github.com/
2. Download Github for Windows
3. Run the installer
4. Create an account on https://github.com/
5. Ask @mroutley to add you to the [IAG team](https://github.com/InfrastructureAnalytics) on GitHub
6. Create an [access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
	
## Configure R

Save .Rprofile to ~/Documents containing:

	library(httr)
	set_config(use_proxy("206.177.43.90",3128))
	Sys.setenv(GITHUB_PAT = "######")
  
This sets RStudio to use the proxy server and your GitHub credentials.

## Optional - Install Swirl

Swirl provides a good, interactive introduction to R.

1. Open http://swirlstats.com/students.html
2. Follow the instructions, starting at step 3
3. Take at least the [R Programming](https://github.com/swirldev/swirl_courses#swirl-courses) course as an introduction to using R