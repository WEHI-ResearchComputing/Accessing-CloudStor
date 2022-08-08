#Code blocks for accessing cloudstor in RStudio. Find the appropritate code for what you want

install.packages("cloudstoR")
library(cloudstoR)
cloud_auth()
# To check what files exist
cloud_list(path = 'cloudstoR Tests')
# To download some data to memory
my_data <- cloud_get(path = 'cloudstoR Tests/mydata1.csv')
# To save a file locally
cloud_put(local_file = '~/datatosave.sav', path = 'additional/path/to/folder', file_name = 'mydata.sav')
# To view file meta data
cloud_meta(path = 'cloudstoR Tests/mydata1.csv')
