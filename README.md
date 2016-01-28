# Branch Build Scripts
Branch Orgs are the place you perform feature development.  These orgs allow you to work within the 'dealer' namespace but not contaminate the master code branch.  A few things to know about Branch Orgs.

1) By default they are empty (No metadata yo)<br />
2) You can modify stuff that the managed codebase may not actually allow<br/>
3) It's a great scratchpad.  If you break something, only you will notice.<br/>

# How do I setup my Branch Org?
Read this, it should help.<br />
<a href="https://dealerteam-prod.mindtouch.us/Internal_Procedures/Feature_Lifecycle/Development/Branch_Org_-_Feature_Branch" target="_blank">Branch Orgs and Feature Development</a>

# Cool, let's populate some Metadata!
If you are ready to prepare your org with a copy of the dealer.master_branch follow these instructions. <br /><br />
First, you will need to have the Force.com Migration Tool (And subsequently ANT) Installed.<br />
Follow these instructions to get it done.<br />
<a href="https://developer.salesforce.com/docs/atlas.en-us.200.0.daas.meta/daas/forcemigrationtool_install.htm" target="_blank">Force.com Migration Toolkit - Installation Instructions<br />
Do yourself a favor and follow the pre-requsites and install ANT.
<hr />

# To populate the metadata
After you clone this repo onto your machine, some settings will need to be applied to make this work.<br />
Open the build.properties file. <br /><br />
<h5>Don't forget to copy the ant-saleforce.jar to the build-branch folder</h5>
<h3>Change the follwing settings</h3>
<ul>
  <li>dt.username = <username> Set your username for the primary managed package here</li>
  <li>dt.password = <password|sectoken> Set your password and sectoken here</li>
</ul>
These auth controls are for copying the source code from the primary packaging org (PPO).
<br />
<br />
Once you have these settings in place it is time to apply your Branch Org User/Pass.
<br />
<ul>
  <li>sf.username = <username> Set your username for your Branch Org Here</li>
  <li>sf.password = <password|sectoken> Set your password and sectoken here</li>
</ul>
<br />
<h3>Retrieve The Packaged Metdata</h3>
Now that your ANT Scripts can authenticate, let's retreive the metadata.<br />
Execute the following command <code>ant retrievePkg</code><br />
This will begin the process of downloading a current copy of the package metadata to your local metadata folder.
<br />
<br />
<h3>You still need to apply the metadata to your Branch</h3>
Execute <code>ant deployCode</code> to send the metadata up to the Branch Org.<br />
<b>This should take about 10 minutes to run, be patient</b>

<br />
That should be all.  The metadata upload should build a working environment for you.



