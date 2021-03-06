### forSteve

#### Getting going with Python

1. How to install ```python3``` 
```
% sudo apt install python3.9
```
2. How to install python3 packages
```
% sudo apt install pip3
...
% vi requirements.txt
<add all the required python packages to the file, one per line>

% sudo pip install -r requirements.txt
```
#### Getting going with Git

```
% sudo apt install git
% cd <top level directory of your project>
% git init
% vi .gitignore
<take a look at https://github.com/github/gitignore/blob/master/Python.gitignore >
% git add .
% git commit -m "initial commit"
```

The above snippet with install git, initialize your project with a git repo, add a ```.gitignore``` file to the project, and add all your existing files to git.  It's important that you not commit secrets to git, because you might push your repo to github.com or another
external site.  If you're using a file like 'secrets.yaml', add that file pattern to the ```.gitignore``` file.

Now, once you make a few changes to your project you can:
```
% git add <select the files to add to the next commit, or their directories>
% git commit  <this will prompt you for a commit message>
```
Some useful commands to learn are:
```
% git status  <show what files have changed>
% git diff    <show the changes>
```
Repeat as needed.

#### Reading a YAML file

Here's how you read a YAML file.  First a sample YAML file. Let's call this ```secrets.yaml```.

```yaml
secrets:
   user: "aUser"
   password: "passWord"
```

Requirements

Add "pyyaml" to your ```requirements.txt``` and run ```% pip3 install -r requirements.txt```

Code

```
import yaml

with open(r'secrets.yaml') as file:
    # The FullLoader parameter handles the conversion from YAML
    # scalar values to Python the dictionary format
    contents = yaml.load(file, Loader=yaml.FullLoader)
    print(f"the secrets are: {contents['secrets']}\n")

# secrets is now a dictionary with two key/value pairs

print(f"The user is \'{contents['secrets']['user']}\'\n")
```

Which produces:

```
% python3 main.py 
the secrets are: {'user': 'aUser', 'password': 'passWord'}

The user is 'aUser'
```

#### Cloning this Repo

Here's how to clone a repo.  This will result a copy of this repo
being placed on your Raspberry Pi, with all of the change history.

```
% cd <a new directory, not underneath the project above>

look at the github UI and click on the CODE tab and then click on the 
GREEN Code button.   Copy the SSH URL that starts with "git@".

% git clone <paste the URL>

done!
```
