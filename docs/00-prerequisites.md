Setup Development Environment
=============================

For the purpose of this playground we will use the next techs:

- NodeJS
- AWS
- AWS CLI
- AWS SAM

NodeJs
------

Let's start with NodeJs. NodeJs is an open-source cross-platform JavaScript runtime environment. A valid analogy is the relation between the Java Virtual Machine and the Java language.

To install node in macOS we will use **node version manager (nvm)** for manage different version node of node in the same machine.

To install **nvm**, open a terminal and copy the next line:

```txt
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
```

In this line we are running a bash script to install the version 0.39.4 of nvm. Below a detailed explanation of the previous line

- `curl`: "Client for URL" is a command for transfer data using various network protocols.
- `|`: The bash pipeline operator to use the standard output of the left command and pipes it as the standard input to the command on the right.
- `bash`: command to specify that the code will be compiled with bash.

To check the **nvm** is installed run:

```
nvm --version
```

The expected output should be:

```
0.39.4
```

Now, we can install NodeJS via nvm running:

```
nvm install -lts
```

Here, we installed the long term support (lts) version of node. To validate that node was installed run:

```
node --version
```

The expected output should be:

```
v20.9.0
```

AWS
---

Amazon Web Service (AWS) is a subsidiary of Amazon than provides on-demand cloud computing platforms and APIs to consumers on a metered, pay-as-you-go basis.

To enable the use of AWS you should create a AWS account. Please follow the [setup AWS sign up](https://docs.aws.amazon.com/SetUp/latest/UserGuide/setup-AWSsignup.html) of the official amazon docs.

Once an account was created we should add a user group in AWS. Follow the next steps to create it:

1. Click on the search bar.
2. Type IAM.
3. Click on the **IAM** service.
4. Look for the **Access management** tab.
5. Check the **User groups** section.
6. Click on the **Create group** button.
7. Define a user group name (e.g., 'admin-group').
8. Check the **Attach permissions policies**.
9. Select the **AdministratorAccess**.
10. Click on the **Create group** button.

With this steps a user group should be create with administrator access. Now we can proceed to create a user for this user group. Again, follow the next steps to create a user.

1. Click on the search bar.
2. Type IAM.
3. Click on the **IAM** service.
4. Look for the **Access management** tab.
5. Check the **User** section.
6. Click on the **Create user** button.
7. Define a user name (e.g., 'admin').
8. Check the **Permissions options**.
9. Select the **Add user to group** box.
10. Check the **admin-group** created previously.
11. Click on the **Create user** button.

There is, now we have the user admin associated to the admin-group. The next step is create an access key and a secret key in AWS to link this user with the AWS command line interface. Please do:

1. Click on the search bar.
2. Type IAM.
3. Click on the **IAM** service.
4. Look for the **Access management** tab.
5. Check the **User** section.
6. Click on the **admin** created before.
7. Go to the **Security credentials** tab.
8. Scroll down to the **Access keys** section.
9. Click on **Create access key**
10. Select the **Command Line Interface (CLI)** box.
11. Add a tag value to describe the purpose of the access key (e.g., use from CLI).
12. Click on **Create access key**.
13. Copy the **Access key** value in your notes app.
14. Copy the **Secret access key** value in your notes app.

Keep in mind that when you close the tab from your browser, you will never get access to the **Secret access key** info.

Finally, let's install and setup the AWS command line interface. The CLI is a unified tool to manage your AWS Services. To process with the installation run in your terminal:

```
curl "http://awscli.amazonaws/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
```

Run the standard macOS installer program specifying the name that we define for the package:

```
sudo installer -pkg ./AWSCLIV2.pkg -target /
```

To verify that the CLI was properly installer run the next command:

```
aws --version
```

The expected output should be:

```
aws-cli/2.13.19 Python/3.11.5 Darwin/22.6.0 exe/x86_64 prompt/off
```

Great! now let's start with the setup to associate our CLI with the user created before via the access key and the secret access key. So, run the next command:

```
aws configure
```

Then specify the requested information:

```
AWS Access Key ID [None]: <your-access-key>
AWS Secret Access Key ID [None]: <your-secret-access-key>
Default region name [None]: us-west-2
Default output format [None]: json
```

This step will create a configuration file in `~.aws/credential`. Before to start using the profile, you should export it:

```
export AWS_PROFILE=default // <your-profile-name>
```

There is, now we can manage our AWS service from the CLI.
