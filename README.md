# 3cx-cti-macos

A library for the [Freshdesk](http://freshdesk.com/) helpdesk cti system for Python 3.

Support for the v2 API CTI

## On the freshdesk platform
You have to be sure that the application 'CTI' has been installed on your platform

## Installation

The easiest way to install is inside a virtualenv and with our python-freshdesk fork (https://github.com/alkivi-sas/python-freshdesk)

1. If you don't have its already, Install Brew, Python3 and virtualenv

First, Install X-Code from the app store

    ```
    $ xcode-select --install
    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ export PATH=/usr/local/bin:$PATH
    ```
Restart your Terminal

    ```
    $ brew install python3
    $ pip install virtualenv
    ```

2. Create the virtualenv (Python 3!) and activate it:

    ```
    $ git clone https://github.com/alkivi-sas/3cx-freshdesk-macos
    $ virtualenv -p python3 3cx-freshdesk-macos
    $ cd 3cx-freshdesk-macos
    $ source bin/activate
    $ git clone https://github.com/alkivi-sas/python-freshdesk.git
    $ pip install ./python-freshdesk
    ```

3. Change the conf file :

    ```
    $ vim freshdesk-example.conf
    ```
Change values with your platform, you can have your caller ID going to a ticket you resolved and you put '.json' at the end of the URL
Example :  https://domain.freshdesk.com/helpdesk/tickets/62.json , you will see responder_id. It is your caller ID.

    ```
    $ mv freshdesk-example.conf freshdesk.conf
    ```
4. Create the log file :
    ```bash
    $ sudo touch /var/log/3cx-freshdesk-macos.log
    $ sudo chmod 766 /var/log/3cx-freshdesk-macos.log
    ```
## Usage
1. From a terminal :

   ```
   $ ./3cx_to_fresdesk.py -c 0836656565
   ```
2. from 3CX softphone on macOS :
Go to parameter --> Advanced --> Enable execute program on inbound calls and put

Path :
   ```
   /Users/myuser/path_of_3cx-freshdesk-macos/bin/python3
   ```     
Parameters :
   ```
   --args /Users/myuser/path_of_3cx-freshdesk-macos/3cx_to_fresdesk.py -c %CallerNumber%
   ```  
