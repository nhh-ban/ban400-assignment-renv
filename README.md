# In-class assignment for renv-lecture


In this assignment, your task is to successfully run the script `renv_test.r`. This script contains three lines, replicated below

```r 
library(dplyr)
x <- data.frame(1)
x %>% ungroup(x)
```

The result should be `1` - not an error. 

The code is inspired by an issue on dplyr where there is a slight change in functionality. In versions *before* `dplyr 1.0.0`, the code works fine. From `1.0.0`, it will fail. See the thread here https://github.com/tidyverse/dplyr/issues/5368. Hadley Wickham argues that the code should indeed fail. 

Do the steps below: 

1. *Verify* that you get an *error* when executing `renv_test.r` with your current version of R (presumably `>= 4.2`).
2. Inspect the `renv.lock`-file in the repo, and determine which R-version this script is intended for. 
3. Go to CRAN and find the appropriate version under "previous releases". Install this legacy-version as you normally would, *except* that you ensure the two boxes under "Registry entries" are *not* ticked off ("Save version number in registry" and "Associate R with .RData-files".)
4. Open the `renv_test.r`-file, and switch to the legacy version of R (you'll need to restart RStudio). 
5. Run `renv::install`, and install the appropriate dependencies. 
6. After installs are successfully completed, try to run `renv_test.r` again in the project's environment. You should now get a `1` as a result. 

Windows-users might have issues with running `renv::install`. This is due to that the default download method in Curl might not be available in Windows. If you normally do not have issues downloading packages, you can try to execute `Sys.setenv(RENV_DOWNLOAD_FILE_METHOD = getOption("download.file.method"))` before running `renv::install`. This makes renv use your default download-method. 





