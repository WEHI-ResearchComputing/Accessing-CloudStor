# Using the CLI

follow the steps below to setup rclone to connect with cloudstor from your cli
-	Download rclone for you machine
-	Type in ```rclone config```
-	enter 'n' in the options
-	Enter Cloudstor as name
-	Enter webdav for storage 
-	Copy webdav address and paste in url prompt (cloudstor site -> settings)
![Screen Shot 2022-08-04 at 11 27 34 am](https://user-images.githubusercontent.com/13778200/184056061-f8486623-5099-4f3a-a707-6ca4bbacf12b.png)
-	ownCloud in vendor prompt
-	enter institute email in user as that is your cloudstor name as well
-	enter your app password (created above) twice to confirm it
-	click enter at the bearer_token prompt
-	then n for advanced config
-	confirm details are correct then quit config

To view files
```
rclone ls CloudStor:/test
```

To copy files between locations 
```
rclone copy <source> <destination>
```
for example to copy from the test folder in cloudstor to a local test folder on ondemand use could use the following
```
rclone copy CloudStor:/test ./test/
```

There are optional parameters that you can use
```
•	--progress: See real-time updates on how the file copying is progressing.
•	--transfers <number>: Specify how many files can be copied at the same time. The default is 4.
•	--create-empty-src-dirs: If you want rclone to preserve the folder structure from the source, even if folders are currently empty.
•	--checkers <number>: Specify how many files and folders rclone can check for updates at once. The default is 8.
```
Using parameters example:
```
rclone copy --progress --transfers 8 CloudStor:/test ./test/
```
