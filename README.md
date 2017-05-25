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
  3) In you home repository add `git remote add live ssh://user@domain.com/home/user/gitdeploy/deploy.git`
  
 
<a name="usage"></a>
Usage
----------
`git push live yourbranch:master`

