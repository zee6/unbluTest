# Precedence Matters {#AgentDeskSetupAndUserGuide-PrecedenceMatters}

It is important to have a broad understanding of how inheritance delivers the power to make wholesale changes easily and why, in order to fully access that power, you must take care to make your changes in the ‘right’ place. Once you have grasped the concept of inheritance, where configurations cascade down through the respective levels, there is another small piece of the inheritance model to bear in mind.

After a configuration parameter is set, the unblu collaboration server will process the parameters set at the most specific, or granular, level at runtime. So, when you set configuration parameters they propagate downwards and when the unblu server is running it picks up, or consumes, those values from the bottommost levels.

There are really three areas where the hierarchical model is present:

1. **Role Hierarchy:**
   Controls permissions and access to features. \(Admin, Supervisor, etc.\)
2. **Level Hierarchy:**
   Defines how configuration parameters cascade down through accounts, teams and user levels \(on the agent side\), and also \(on the visitor side\) from accounts through domains and APIKeys.
3. **Runtime Precedence:**
   Decides exactly which parameters are consumed by the unblu collaboration server at runtime according to which value sits at the lowest node in the hierarchy.

## Role Hierarchy versus Level Hierarchy versus Runtime Precedence {#AgentDeskSetupAndUserGuide-RoleHierarchyversusLevelHierarchyversusRuntimePrecedence}

* The role hierarchy defines ‘what’ configuration parameters a role can see and change.
* The level hierarchy describes the structures within which configuration parameters are set.
* The runtime precedence defines which parameters are consumed by the unblu collaboration server. 

### Level Inheritance Model for the Visitor Side {#AgentDeskSetupAndUserGuide-LevelInheritanceModelfortheVisitorSide}

Here is the order of how configuration parameters cascade down through the inheritance tree on the visitor side:

Global \(Settings\) &gt; Account \(Settings\) &gt; Domains \(Edit domain &gt; Settings\) &gt; API Keys \(Edit APIKey &gt; Settings\)

### Runtime Precedence Model for the Visitor Side {#AgentDeskSetupAndUserGuide-RuntimePrecedenceModelfortheVisitorSide}

Here is the order of how the unblu collaboration server will process configuration settings on the visitor side during runtime \(Runtime Precedence\):

API Keys \(Edit APIKey &gt; Settings\)  &gt; Domains \(Edit domain &gt; Settings\) &gt; Account \(Settings\) &gt; Global \(Settings\)

### Level Inheritance Model for the Agent Side {#AgentDeskSetupAndUserGuide-LevelInheritanceModelfortheAgentSide}

Here is the order of how configuration parameters cascade down through the inheritance tree:

Global \(Settings\) -&gt; Account \(Settings\) -&gt; Teams \(Edit team &gt; Settings\) -&gt; Users \(Edit user &gt; Settings\)

### Runtime Precedence Model for the Agent Side {#AgentDeskSetupAndUserGuide-RuntimePrecedenceModelfortheAgentSide}

Here is the order of how the unblu collaboration server will process configuration settings on the agent side during runtime \(Runtime Precedence\):

Users \(Edit user &gt; Settings\) &gt; Teams \(Edit team &gt; Settings\) &gt; Account \(Settings\) &gt; Global \(Settings\)

Changes you make higher up in the dependency tree propagate downwards. However, and this is a crucial point in understanding the hierarchy, downstream configurations are the ones that the unblu collaboration server uses to populate your system. Whatever configuration parameter is set at the lowest node \(at the bottom\) of any given dependency tree is the configuration parameter that the running system will consume. For example, if you set the language for the help function \(Key:`com.unblu.core.gearmenu.gearMenuUriHelpSupportedLanguages`\) to be English \(en\) higher up in the tree but a particular agent at the bottom of the tree is set to Italian then that agent will see Italian while all other agents see English because the unblu collaboration server will pick up the setting for Italian for that particular agent and use the inherited values/defaults for the others.

All that matters when you are setting configurations is ‘where’ they are set, not by whom they are set. So, if you \(no matter whether you are a Super Admin or Admin or a Supervisor\) can see the parameter and it allows you to change it you must take care that the configuration parameters deliver what you expect. And if they do not deliver what you expect it may be that a parameter has been set ‘downstream’ that is taking precedence over something you set higher up in the hierarchy. A simple example would be an Admin setting a configuration parameter that will propagate down to supervisors and agents below the Admin level, then a supervisor alters the setting which would take precedence and propagate down through the agents below them in the hierarchy, thus changing the setting from that intended by the Admin.**Note that this is how the product is designed to function.**

If you set a configuration parameter to ‘A’ at the Account level and set the same parameter to ‘B’ at the Domain level then the parameter that will be used at runtime is ‘B’. And if you then set the same parameter at the APIKeys level to ‘C’ then ‘C’ will take precedence over ‘A’ and ‘B’.

Imagine a large organization that has a single domain but wants their site instrumented with two \(or more\) different versions of unblu. For example, one version uses ‘chat only’ and the other uses ‘PIN only’, then you could define whether unblu uses chat or PIN at the APIKey level using two, or more, generated API keys to differentiate between the functionality applied to a single Domain. In practice this simply means defining the parameter\(s\), in this case, at:

**Account &gt; APIKeys &gt;**\(Click the pencil \(Edit\) icon then the Edit APIKey modal window slides in from the right\)**&gt; Settings**\(here you would make the changes that will be consumed by the unblu collaboration server at runtime\)

The point here regarding hierarchies is that the same results could be obtained by setting configuration values at the Domain level. And if these two settings are at odds with each other then the net effect could cause significant problems.

## Inheritance Troubleshooting Tips {#AgentDeskSetupAndUserGuide-InheritanceTroubleshootingTips}

In the Agent Desk, configuration parameters that have been changed are colored dark gray. Configuration parameters that have not been changed from the default values are light gray.

Some default values are ‘factory defaults’ while others are defaults by virtue of the fact that they were set somewhere higher up in the tree. An example might be language, where the default at the Global level is English and German. If these languages are changed, at the Global level, to English, German, and Spanish then the unblu collaboration server will read the change at the Global level as a default for levels below Global. See the pictures below:

![](https://www.unblu.com/confluence/download/thumbnails/102793956/Precedence_1.png?version=1&modificationDate=1479740456000&api=v2)

The picture above is what this example looks like in the Agent Desk at the**Global level**. It shows that Spanish has been added \(Configured: de,en,es\) to the default \(English \(en\) and German \(de\)\) languages.

![](https://www.unblu.com/confluence/download/thumbnails/102793956/Precedence_2.png?version=1&modificationDate=1479740529000&api=v2)

The picture above is what this example looks like when viewing from the Agent Desk at the**Account level**. At the Account level the new default is the setting that was made \(in Global\) to add Spanish to the default. Now it is interpreted as the default at the Account level and a further change has been made at this \(Account\) level, to use only English and Spanish. Therefore, the unblu server will consume the English and Spanish parameters to be used for all agents within this account \(unless the configuration parameters are further changed at a level below Account\).

When troubleshooting, check the most ‘granular’ level first to see if it matches what you think you should be seeing. For example, as the APIKey level will trump the Domains, Account and Global Settings during runtime, then make sure you know what settings have been changed first in the APIKey Settings, then work your way up the tree through Domains then Account then Global.

Use the ‘i’ icon beside the configuration value \(in Settings\) to view inheritance information. To see a little more information about the configuration value use the Advanced button then, from the Options menu, select Technical Labels. In this way you can see the default \(or inherited\) value and the values that have been altered.

