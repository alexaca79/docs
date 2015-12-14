# Setup guide for IAG toolchain

## Install R

1. Open http://cran.rstudio.com/ , click the "Download R for Windows" link and then the "base" link
2. Download the R for Windows installer
3. Run the installer

## Install RStudio

1. Open http://www.rstudio.com/products/rstudio/download/

If you **have** admin rights:

2. Download the Installer for Windows XP
3. Run the installer

If you **do not have** admin rights:

2. Download the Zip/Tarballs archive for Windows XP (you can't run the installer without admin rights to your computer)
3. Right-click on the downloaded archive,  select "Extract all...", and extract the contents to an RStudio folder in your My Documents folder
4. Create a shortcut to the bin/rstudio.exe file by right-clicking on the file and choosing "Send to > Desktop"

## Install devtools & Rtools

### devtools
1. In the command line type `install.packages("devtools")`
2. The devtools package can now be found in the **Packages** tab (bottom left of screen)
3. To import the package to be used you can either check the devtools checkbox or type `library(devtools)` in the command line

### rTools
1. Open http://cran.r-project.org/bin/windows/Rtools/
2. Download and install the most recent Rtools
3. Use `devtools::find_rtools()` in RStudio to test that the download worked

If rTools is not found:

4. Use the following code (This code assumes the rTools folder is saved to the C:/ drive)
```r
library(devtools)
add_path("C:\\Rtools\\bin", after = 1)
add_path("C:\\Rtools\\gcc-4.6.3\\bin", after = 2)
```

5. Use `devtools::find_rtools()` again to test for rTools

If this fixes the code, but the problem presents itself everytime you reset RStudio:

6. Add the above code to **.RProfile** in the home directory
    + The home directory is *usually* "My Documents" but can be found using `getwd()`
    + If .RProfile does not exist you may need to create it yourself
7. (Optional) To test for rTools each time you open RStudio, add the following code to .RProfile
```r
print("rTools found?")
find_rtools()
```
	
## Install git

1. Open https://windows.github.com/
2. Download Github for Windows
3. Run the installer
4. Open the Github for Windows options menu (the gear icon in the top right) and set the Default shell to Git Bash 
5. Add the following lines to the file `C:/users/USERNAME/.gitconfig`

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
2. Email Wendy at Wendy.D.Elliott@ontario.ca to add you to the [IAG team](https://github.com/InfrastructureAnalytics) on GitHub
3. Create an [access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
    + Save the code it gives you because we will be needing it for the next step (denoted as "######")
	
## Configure RStudio

1. Add the following code to **.Rprofile**:
```R
library(httr)
set_config(use_proxy("206.177.43.90",3128))
Sys.setenv(GITHUB_PAT = "######")
```
    + If .RProfile does not exist, follow the steps found in the RTools section (part 6)
    + This sets RStudio to use the proxy server and your GitHub credentials.

2. In RStudio, use the Tools dropdown to open the Global Options
3. Select the Git/SVN tab
4. For the Git executable: 
    + browse to `C:\Users\USERNAME\AppData\Local\GitHub\`
    + click into `PortableGit_xxxxx` (where xxxxx is a random set of characters)
    + if you are on a **32-bit** machine, click into `mingw32`
    + click into `bin`
    + double-click on `git.exe`

## Optional - Install Swirl

Swirl provides a good, interactive introduction to R.

1. Open http://swirlstats.com/students.html
2. Follow the instructions, starting at step 3
3. Take at least the [R Programming](https://github.com/swirldev/swirl_courses#swirl-courses) course as an introduction to using R
