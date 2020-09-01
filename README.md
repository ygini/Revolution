# Revolution

Warning: work in progress, do not use this project at this time! The current documentation isn't the current working state but the final goal.

Description 
===================================

**Revolution** for macOS is a fork and evolution of the original [**Privileges** Open Source app published by SAP](https://github.com/SAP/macOS-enterprise-privileges).

**Privileges** by SAP is made to let the user be admin or non admin on demand. The mindset behind the app and the implemented behavior is made to empower users by giving them privileges. 

One of the limitation of this way of doing things is the ability to automatically remove authorization after a certain period of time, and to consider that everyone must be standard in a normal situation.

**Revolution** is an evolved fork to "abolish" privileges. The mindset behind this way of doing things is to consider that everyone must be equal and standard by default. And on demand, exceptional rights for exceptional situation can be given but for a limited amount of time. The return to the standard situation is automatic.

Requirements
===================================

**Revolution** supports the following macOS versions:

* macOS 10.12.x
* macOS 10.13.x
* macOS 10.14.x
* macOS 10.15.x
* macOS 11.x

Installation
===================================

1. Log into your Mac using an account with admin privileges.

2. Download **Revolution.pkg**.

3. Install **Revolution.pkg** to automatically deploy all needed services and helper agent.

Using Revolution
===================================

By default, **Revolution** does not provide any user interface, just a command line that you can trigger from the user land. It will detect the calling user and will add it to the list of privileged users for the defined amount of time (15 minutes by default).

`/Library/Application Support/com.github.ygini.revolution/bin/revolution`

If you want to clear all current temporary privileges without waiting for the expiracy time, use the same command with the `-cleanup` argument.

`/Library/Application Support/com.github.ygini.revolution/bin/revolution -cleanup`

Temporary privileges are automatically cleaned on logout, but not during fast user switching.

Once sent, the request will have to be authenticated by the end user via a system login request (with Touch ID support) initiated by the helper agent.

This provide some kind of layered access filter where one process send the request, and the other ask to the user if the request is legitimate.


Helper Tools
===================================

The following helper tools are installed to allow **Revolution** the necessary access rights to grant or remove admin rights:

`/Library/PrivilegedHelperTools/com.github.ygini.revolution.helper`

`/Library/LaunchDaemons/com.github.ygini.revolution.helper.plist`

For more information on privilege elevation using a privileged helper app and LaunchDaemon, please see the link below:

[https://developer.apple.com/library/archive/documentation/Security/Conceptual/SecureCodingGuide/Articles/AccessControl.html](https://developer.apple.com/library/archive/documentation/Security/Conceptual/SecureCodingGuide/Articles/AccessControl.html)


Frequently Asked Questions
===================================

### How do I uninstall Privileges.app?

1. Ensure that your user account has admin rights. If needed, launch **Revolution** one final time to make sure you have them.
2. Remove the following files:

* `/Library/Application Support/com.github.ygini.revolution`
* `/Library/PrivilegedHelperTools/com.github.ygini.revolution.helper`
* `/Library/LaunchDaemons/corp.sap.privileges.helper.plist`

Application Management
===================================

It is possible to manage settings for **Revolution** using a macOS configuration profile. [For more details, please click here](managed_settings).

Security
===================================
 Found a security-related issue or vulnerability and want to notify us? Please fill a bug report or contact Yoann Gini on any private channel you can find (Twitter, MacAdmins' Slack, etc.).

License
===================================
This file is licensed under the Apache Software License, Version 2.0 except as noted in the [LICENSE](LICENSE) file. 

SUBCOMPONENTS

This project is a fork of **Privileges** by SAP SE or an SAP affiliate company, also published under the Apache Software License, Version 2.0.

This project includes the following Apple `EvenBetterAuthorizationSample` sample code, which is subject to separate license terms.
Your use of the code included in this project is subject to the separate license terms applicable to
the Apple sample license code.

* Component: [Common.h](https://developer.apple.com/library/archive/samplecode/EvenBetterAuthorizationSample/Listings/Common_Common_h.html#//apple_ref/doc/uid/DTS40013768-Common_Common_h-DontLinkElementID_12) 
* Component: [Common.m](https://developer.apple.com/library/archive/samplecode/EvenBetterAuthorizationSample/Listings/Common_Common_m.html#//apple_ref/doc/uid/DTS40013768-Common_Common_m-DontLinkElementID_13)
* Component: [HelperTool.h](https://developer.apple.com/library/archive/samplecode/EvenBetterAuthorizationSample/Listings/HelperTool_HelperTool_h.html#//apple_ref/doc/uid/DTS40013768-HelperTool_HelperTool_h-DontLinkElementID_14) 
* Component: [HelperTool.m](https://developer.apple.com/library/archive/samplecode/EvenBetterAuthorizationSample/Listings/HelperTool_HelperTool_m.html#//apple_ref/doc/uid/DTS40013768-HelperTool_HelperTool_m-DontLinkElementID_15)

For more details, please see the the [LICENSE](LICENSE) file. 
