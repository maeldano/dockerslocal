FROM rocker/tidyverse
MAINTAINER Mark Edmondson (r@sunholo.com)

# install cron and R package dependencies
RUN apt-get update && apt-get install -y \
    cron \
    nano \
    libxml2-dev \
    default-jre \
    openssh-server \
    openssh-client \
    proj-bin \
    libgdal-dev \
    libproj-dev \
    gdal-bin \
    ## clean up
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/ \     
    && rm -rf /tmp/downloaded_packages/ /tmp/*.rds
    
## Install packages from CRAN
RUN install2.r --error \ 
    -r 'http://cran.rstudio.com' \
    googleAuthR shinyFiles googleCloudStorageR \
    bigQueryR gmailr googleAnalyticsR cronR googleComputeEngineR anytime Quandl caret sp searchConsoleR data.table anytime corrplot zoo xts forecast xgboost e1071 doParallel earth rpart party deepboost kernlab glmnet Matrix kknn LiblineaR RSNNS keras h2o stringr digest reshape2 Rcpp RCurl jsonlite curl httr sp protoclass randomForest proxy gbm klaR naivebayes stepPlr obliqueRF rgdal tictoc fasttime \
    ## install Github packages
    && Rscript -e "devtools::install_github(c('MarkEdmondson1234/googleLanguageR'))" \
    ## clean up
    && rm -rf /tmp/downloaded_packages/ /tmp/*.rds \

## Start cron
RUN sudo service cron start