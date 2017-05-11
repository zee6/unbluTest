# 

# Introductio {#AgentDeskSetupAndUserGuide-Introduction}

This document is designed to get you up and running with unblu. It will take you through all of the features of the Agent Desk and show you, in simple steps, how to implement them.

This document also attempts to explain unblu in light of the actual business processes you wish to instigate, or integrate with your current processes or ambitions. Once you have become familiar with unblu’s Agent Desk you will be able to project your ideas into your own, unique, fusion of process and technology.

unblu cannot know your internal processes so we advise you to go through this document at a leisurely pace. Set up some dummy users and teams and play around with them until you can see how to build your entire customer-engagement strategy around unblu’s Agent Desk.

We would also encourage users of all levels/roles to read through parts of this document that may not seem relevant to their tasks as it will allow insight into the complete structure and how they fit into that structure. This is important as, when properly configured, the whole system can act as a single ‘customer-engagement machine’ with each and every agent contributing to what looks, to the visitor, like a seamless, single ‘intelligence’ while offering the personal touch of each individual agent.

## 1.1.The Hierarchical Nature of the Model {#AgentDeskSetupAndUserGuide-TheHierarchicalNatureoftheModel}

The unblu Agent Desk uses a system of hierarchy/inheritance. This means that business models must/will reflect this hierarchy.

While the Super Admin role must be filled by an experienced technical person, all other roles below this level \(from Admin to Registered User\) represent business roles. And while this design may seem restrictive at first blush it is highly-configurable, makes it easy to manage, and provides a logical framework in which to build efficient teams and processes.

**Note:**Each person can only be assigned one single role. This is both in order to comply with security considerations and to simplify the potential complexity involved when setting up an efficient customer-engagement infrastructure.

unblu’s design makes it easy to propagate changes through the system without ‘interfering’ with any real-life customer-engagement professionals who need only to deal with customers.

### 1.1.1.The Super Admin {#AgentDeskSetupAndUserGuide-TheSuperAdmin}

The scope of the Super Admin is ‘everything’. The difference between an Admin and a Super Admin is that the Super Admin can see the Global item in the menu. The essential difference in functional terms is that a Super Admin can create and manage accounts while an Admin role cannot. The Admin role can change and manipulate virtually everything outside of creating accounts and should therefore be considered the highest role in your system design.**The role of Super Admin can only be employed in on-premise installations.**There is simply no need for a Super Admin within our cloud solution. Even within on-premise installations it is unlikely that more than a single Super Admin would be required. Very large organizations who operate on a global basis may see a need to create multiple accounts if they have many differing teams spread across large geographical, linguistic, and business areas. Only a Super Admin can create other Super Admins.

### 1.1.2.The Admin User {#AgentDeskSetupAndUserGuide-TheAdminUser}

Below the Super Admin in the hierarchy is the Admin user. This is the highest business role in the design. The Admin user can make changes that will propagate down through their own team \(and any ‘child’ teams of the parent team of which the Admin is a member\). The Admin user ‘sees’ everything and can manipulate everything within an account \(outside of creating Super Admins\).

If you want to ‘redesign’ the interface to reflect corporate standards and branding or you want to alter the functionality, then these changes can easily be implemented at the Admin level. For example, the look-and-feel \(branding, corporate standards, etc.\) can be set at the Admin level and these changes will propagate down through all roles in that account. So, changing the colors to green and blue at the highest level \(Admin\) will change colors at all levels below. It means that changes across multiple teams and users can be made without any \(active\) reference at all to the levels below. An Admin can make changes across all teams and users and those changes are inherited by all teams and team members. Similarly, all roles can make changes, according to a subset of the complete configuration options below their level but cannot make any changes above their level. Users with the Admin role are able to create as many other Admin roles as they wish but cannot create Super Admins.

### 1.1.3.The Supervisor {#AgentDeskSetupAndUserGuide-TheSupervisor}

Below the Admin user is the Supervisor role. The Supervisor can see all members of their own team and can use the various tools available to run that team efficiently. The Supervisor can also create and edit Registered Users in their own team. Only a small subset of some configuration items are available to the supervisor role as it is designed to serve the needs of a real-life supervisor, and indeed to deliberately keep technical complexities out of their scope.

### 1.1.4.Registered Users {#AgentDeskSetupAndUserGuide-RegisteredUsers}

These are all users known to the system who are not Super Admins or Admins or Supervisors. The Registered user role is designed to keep all technical considerations elsewhere and allow agents to simply engage with the customer.

**Note:**There is a role below Registered user in the hierarchy: Web user, which means a user not known to the system. We would strongly advise you to only allow Registered user roles, and above, to manipulate or engage with your system in any way.

### 1.1.5.Teams {#AgentDeskSetupAndUserGuide-Teams}

Teams are also arranged in a hierarchical design. This means that you can set ‘parent’ and ‘child’ teams in the hierarchy. The Supervisor of a parent team can ‘see’ users in a team that is a child of the team of which he is a member, while the Supervisor of a child team can only see users in his own team. These distinctions can be turned into business models as, for example, a parent team might be populated by portfolio analysts who engage with high-value clients. But if the customer in a session with a portfolio analyst asks about a loan or a given financial instrument, the Supervisor of the parent team will be able to see who is available to serve that client in the child teams and forward the session to the appropriate member of a child team.

## 1.2.Design Strategy {#AgentDeskSetupAndUserGuide-DesignStrategy}

You must take care to design how the hierarchy is structured in reference to your business needs. For example, it may be tempting to set the highest parent team as, for example, portfolio analysts and set child teams progressively under that team. Depending on your goals this may be the right structure. But it may be that your organization is very large and receives many enquiries across the globe for many services. In this case the parent team might be the initial front-line interface with the customer. And in this case you may want the highest-level \(parent\) team to be your initial contact people who ‘answer queries’. They can assess what the visitor wants and can then forward the session to the internal contact who can maximize your sales and service efforts.

Although you can create and edit users and teams at any time, an easy way to get started is to create users, create teams, then allocate the users to the teams. In the next section we will create some users then create some teams. Finally, we will assign the users to their teams. This will get you started and, as soon as you can create these entities, it will become clearer to you how to apply these structures to the skills and human resources available in your organization.

After creating the users and teams we will look at some of the monitoring and statistical tools. Finally, we will look at the Canned responses before some instructions for the Super-Admin on how to handle migrating your configurations when unblu is upgraded.

After working through this whole document you will have a clearer idea of how you want to integrate unblu with your current processes.

**Note:**If you already have your own identity management system and intend to use the unblu User Management Synchronization Tool in order to automatically populate the unblu database with your users and organizational structures you should know that you must take care when configuring the Synchronization Tool. Your synchronization strategy can have an effect on the functionality of the unblu Agent Desk. You can still manipulate the Agent Desk as described here but you must employ the correct synchronization strategy to ensure that the right data is being synchronized in the right way. For more on this topic see:[https://www.unblu.com/en/doc/latest/user-management-synchronization-tool-specification](https://www.unblu.com/en/doc/latest/user-management-synchronization-tool-specification)

## 1.3.Thoughts on Modelling {#AgentDeskSetupAndUserGuide-ThoughtsonModelling}

When you are considering how to structure the agent desk keep the following in mind: You want the whole design to enable you to draw a direct line between a visitor to your web site and the optimal agent \(for that particular visitor\) within your company. Every decision you make regarding design should have an overarching picture of how to get exactly the right person or team communicating with a visitor.

