# Assignment 2_1 - Jenkins

## Installing Blue Ocean
- Go to  `Manage Jenkins > Manage Plugins`.
- Choose the `Available` tab and search for `blue ocean`.
- Select the `Blue Ocean (BlueOcean Aggregator)` plugin.
- Restart `Jenkins` and choose the `Blue Ocean` option from the left menu to use the Blue Ocean UI.

## Using a private GitHub Repository
- Create a new freestyle project.
- Under `Source Code Management` select `Git`.
- Add the private repository's URL in the `Repository URL` text box.
- Click on `Add` button next to `Credential` text box as the repo is private.
- Chose the preferred authentication method and provide the credentials.
- Enter GitHub username and password.
- Choose the newly added credentials in the dropdown menu that appears next to `Credentials` label.
- Now the private repository can be used with Jenkins like any other repository.

## Using Git SCM Poll

### Configuring build triggers
- In the configuration page, set build triggers to `GitHub hook trigger for GITScm polling`

### Adding Jenkins service to GitHub
Now we need to set up our GitHub repo to make a request to Jenkins webhook so that the polling logic can be applied.
- Go to GitHub repo and navigate to `Settings`.
- Choose `Webhooks` from the submenu.
- Add `http://<public-ip or URL>/github-webhook` under `Jenkins hook url`.
- Now GitHub is cofigured to send a request when a commit is made.

## Post Build Actions - Extended Email Notification

### Configuring Email
We need to first add the details of the SMTP credentials so that Jenkins can send the mail.

- Go to `Manage Jenkins > Configure Systems` and scroll down to the `E-mail Notification` section.
- Add the SMTP server details.
- Click on the `Advanced` button to configure the mail account used to send the mails.
- Select `Use SMTP Authentication`.
- Enter the account username and password.
- Select `Use SSL` and specify the `SMTP port`.
- Select `Allow sending to unregistered users` if mail should be sent to non-Jenkins users.
- With this the basic email configuration is complete.

### Adding the post build action
- Go to Post-build Actions section in the Configuration page of project.
- Click on `Add post-build action` and choose `Editable Email Notification`.
- The options can be used for project based customizations of the email notification.

With this the Post build action for extended email notification is complete.
