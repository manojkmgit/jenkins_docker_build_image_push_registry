1. Create app password and prepare the repo url

https://bitbucket.org/account/admin/app-passwords

Take note of username of bitb account and copy the newly created app password.

#Repo url will be in format.

#https://USERNAME:APP_PASSWORD@bitbucket.org/OWNER/REPO.git

#For ex:

#https://manojkmbit:HB49KB6BPLVzCqb@bitbucket.org/manojkmbit/mycode.git

#Please make sure you have a file named Jenkinsfile in you repo that will have all the steps of build/test/deploy etc)

2. Create webhook in Bitbucket

https://bitbucket.org/manojkmbit/<your-repo-name>/admin/webhooks

For ex:

https://bitbucket.org/manojkmbit/mycode/admin/webhooks

Give some title.

In Url, enter Jenkins server url

https://JenkinsserverURL/git/notifyCommit?url=https://bitbucket.repository-link/repository.git

For ex:

https://http://192.168.0.111/git/notifyCommit?url=https://bitbucket.org/manojkmbit/mycode.git

3. Install "Bitbucket" and "Pipeline" plugins in jekins and restart jenkins.

4. Jenkins -> Manage Jenkins -> Manage Credentials -> Add new cred for BITB. Your username and app password generated earlier.

5. Create a new item and select Pipeline type.

On "Build Triggers" tab:

Select Checkbox for - "Build when a change is pushed to BitBucket"

On "Advanced Project Options" tab:

Definition -> Pipeline script from SCM

SCM -> Git

Repository URL -> Enter your repo url and select the earlier created credential from the dropdown.

Branches to build -> set to main or master or whatever is in your project repo

Script Path -> Jenkinsfile (you should have a file named Jenkinsfile in you repo that will have all the steps of build/test/deploy etc)

6. Go to item and click on "Build Now"

7. Go down to "Build History" and open the current build

8. Click on "Console Output"
