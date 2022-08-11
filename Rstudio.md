# RStudio

https://github.com/pdparker/cloudstoR

You may have to install some axillary packages for cloudstoR to work
The connection to cloudstor can sometimes be dodgy, if you have followed the instructions and get stuck giving a 403/401 error, keep trying the command it should work at some point.

Log in to Cloudstor and sign up with your WEHI email address, account will be ready to go.
You will need your Cloudstor username (WEHI email) and password to use the API, however it is not your regular cloudstor password. You will need to create an app password by following these steps - https://support.aarnet.edu.au/hc/en-us/articles/236034707-How-do-I-manage-change-my-passwords-
Open RStudio however you like to run it.
Run the following commands:
```
install.packages("cloudstoR")
library(cloudstoR)
```

This will have downloaded and loaded cloudstoR into your R session. 
To authenticate yourself use the following command and enter your username and password when prompted, this will stop you needing to enter it everytime you call a function. You can use this again to reset your name and password. If you need to revoke your app password you can use reset_keys=TRUE which removes the authentication.
```
cloud_auth()or cloud_auth(reset_keys=TRUE)
```

To list the data found in your cloudstor account use the following:
```
cloud_list(path = 'cloudstoR Tests')
#> [1] "Another Folder/" "mydata1.csv"     "mydata2.csv"
```

To retrieve a specific file from cloudstor use the cloud_get() function and provide the correct path to the file. This will read the file to memory not download it to the system.
```
my_data <- cloud_get(path = 'cloudstoR Tests/mydata1.csv')
my_data
#>   A  B  C
#> 1 3 10  8
#> 2 5  7  5
#> 3 5  7 10
```

To save a local file to cloudstor navigate to the Choose Directory menu option and find where your local file is held, or have the path to it to add to the command. The use the cloud_put command to add the file to your cloudstor account. 


![Screen Shot 2022-08-01 at 4 57 12 pm](https://user-images.githubusercontent.com/13778200/184055833-2a3d624d-f1a4-4dc8-ae6f-ce8af11f1bcd.png)


```
cloud_put(local_file = '~/datatosave.sav',
          path = 'additional/path/to/folder',
          file_name = 'mydata.sav')
```
If youre not sure where the file you require is, use the cloud_browse() function and navitage the menus using the number keys as shown.


![Picture1](https://user-images.githubusercontent.com/13778200/184055813-25d72ece-c501-4b06-a80b-6d8d461d2a66.png)



You can view the meta data of a file using the cloud_meta() command
```
cloud_meta(path = 'cloudstoR Tests/mydata1.csv')
#>                                             file_name
#> 1 /plus/remote.php/webdav/cloudstoR Tests/mydata1.csv
#>                                  tag                 file_modified file_size
#> 1 "9a2a8fdd58a6c2746cd65b7dace6115c" Sun, 16 Jan 2022 05:42:52 GMT        36
```
