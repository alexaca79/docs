# Setup guide for IAG toolchain

## Install R

1. Open http://cran.rstudio.com/ , click the "Download R for Windows" link and then the "base" link
2. Download the R for Windows installer
3. Run the installer

## Install Rtools

1. Open http://cran.r-project.org/bin/windows/Rtools/
2. Download and install the most recent Rtools
3. Use **find_rtools()** in RStudio to test that the download worked

If rTools is not found:

4. Use the following code (This code assumes the rTools folder is saved to the C:/ drive)
```r
library(devtools)
add_path("C:\\Rtools\\bin", after = 1)
add_path("C:\\Rtools\\gcc-4.6.3\\bin", after = 2)
```

If this fixes the code, but the problem presents itself everytime you reset RStudio:

5. Add the above code to **.RProfile**
6. (Optional) To test for rTools each time you open RStudio, add the code below
```r
print("rTools found?")
find_rtools()
```


## Install RStudio

1. Open http://www.rstudio.com/products/rstudio/download/

If you **have** admin rights:

2. Download the Installer for Windows XP
3. Run the installer

If you **do not have** admin rights:

2. Download the Zip/Tarballs archive for Windows XP (you can't run the installer without admin rights to your computer)
3. Right-click on the downloaded archive,  select "Extract all...", and extract the contents to an RStudio folder in your My Documents folder
4. Create a shortcut to the bin/rstudio.exe file by right-clicking on the file and choosing "Send to > Desktop"
	
## Install git

1. Open https://windows.github.com/
2. Download Github for Windows
3. Run the installer
4. Open the Github for Windows options menu (the gear icon in the top right) and set the Default shell to Git Bash 
5. Add the following lines to ~/.gitconfig

```
[url "https://"]
	insteadof = git://
[http]
	proxy = http://206.177.43.90:3128
[https]
	proxy = https://206.177.43.90:3128
```

## Setup github

1. Create an account on https://github.com/
2. Ask @mroutley to add you to the [IAG team](https://github.com/InfrastructureAnalytics) on GitHub
3. Create an [access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
	
## Configure RStudio

Save .Rprofile to ~/Documents containing:

```R
library(httr)
set_config(use_proxy("206.177.43.90",3128))
Sys.setenv(GITHUB_PAT = "######")
```

This sets RStudio to use the proxy server and your GitHub credentials.

Now open the Global Options list in RStudio and select the Git/SVN tab. For the Git executable, browse to: 

    C:\Users\USERNAME\AppData\Local\GitHub\PortableGit_c2ba306e536fdf878271f7fe636a147ff37326ad\bin\git.exe
    
where `USERNAME` is your windows username.

## Optional - Install Swirl

Swirl provides a good, interactive introduction to R.

1. Open http://swirlstats.com/students.html
2. Follow the instructions, starting at step 3
3. Take at least the [R Programming](https://github.com/swirldev/swirl_courses#swirl-courses) course as an introduction to using R
