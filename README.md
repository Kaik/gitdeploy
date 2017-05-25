GitDeploy
===================================

  1. [Introduction](#introduction)
  2. [Requirements](#requirements)
  3. [Installing](#installing)
  4. [Usage](#usage)
<a name="introduction"></a>
Introduction
------------
Small "program" in bash to use git as deployment system

<a name="requirements"></a>
Requirements
------------
You need externall server with ssh and git 

Please note:

 - Composer is needed as well if you want to compose

<a name="installing"></a>
Installing
----------
Installation in steps

  1) In you account home folder on externall server execute `git clone https://github.com/Kaik/gitdeploy.git  `
  2) Once finished install with `./gitdeploy/install`
  3) In your local working repository add `git remote add live ssh://user@domain.com/home/user/gitdeploy/deploy.git`
  
 
<a name="usage"></a>
Usage
----------
There are various ways how you can make use of git bare repository with git hooks for all sorts of deployments, backups.
gitdeploy/post-receive directory contains branch handlers. You can create your own with your own branch name then when you push to this branch
`git push live localbranch:yourbranch ` your handler will execute. 

Please look into `gitdeploy/config` for configuration options

Note:
 - Because git is calling hooks only if there is a change in code you need to add empty commit and then push if you want to trigger some functionality without changing actuall code.
`git commit --allow-empty -m 'push to execute post-receive'` 
 - Master branch handler does not do much it is just a template for your custom handlers

```
 git push live localbranch:master                                                                                                                                     
Enter passphrase for key 'yourserversshkey': 
stdin: is not a tty
Counting objects: 144499, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (39736/39736), done.
Writing objects: 100% (144499/144499), 52.28 MiB | 99.00 KiB/s, done.
Total 144499 (delta 98360), reused 143954 (delta 97849)
remote: Resolving deltas: 100% (98360/98360), done.                                                                                                                                                    
remote: Config loaded from: /home/useraccount/gitdeploy/config                                                                                                                                            
remote:    /===============================                                                                                                                                                            
remote:    | DEPLOYMENT                                                                                                                                                                                
remote:    | Date     : 20170525-1357                                                                                                                                                                  
remote:    | Received Push Request at 2017-05-25                                                                                                                                                       
remote:    | Old SHA: 0000000000000000000000000000000000000000                                                                                                                                         
remote:    | New SHA: d45da545a6d0c753d3f62269f773f64f36a2f80b                                                                                                                                         
remote:    | Branch Name: master                                                                                                                                                                       
remote:    | Running branch handler master                                                                                                                                                             
remote:    | Working tree: /home/useraccount/gitdeploy/workingtree                                                                                                                                        
remote:    | Working tree cleaned                                                                                                                                                                      
remote:    | Running git!                                                                                                                                                                              
remote:    | Git done! - logfile: /home/useraccount/gitdeploy/logs/git-20170525-1357.log                                                                                                                  
remote:    | Working tree ready! in /home/useraccount/gitdeploy/workingtree                                                                                                                               
remote:    | Running common/compose-tree! - this will take a while                                                                                                                                     
remote:    | Common/compose-tree done! - logfile: /home/useraccount/gitdeploy/logs/composer-20170525-1357.log                                                                                             
remote:    | Zikula deploy tree started                                                                                                                                                                
remote:    | Deploying from: /home/useraccount/gitdeploy/workingtree                                                                                                                                      
remote:    | Files deployed to: /home/useraccount/public_html                                                                                                                                             
remote:    | Zikula autoload fix started                                                                                                                                                               
remote:    | Fixing files...                                                                                                                                                                           
remote:    | Files fixed in: /home/useraccount/public_html                                                                                                                                                
remote:    | Branch handler master finished!                                                                                                                                                           
remote:    /===============================                                                                                                                                                            
To ssh://useraccount@serversshkey/home/useraccount/gitdeploy/deploy.git
 * [new branch]      localbranch -> master

```

