# Zero Trust Enforcement with Conditional Access Policies in Entra ID

## Project Overview
This project demonstrates the implementation of Zero Trust security principles within a Microsoft 365 environment by leveraging Microsoft Entra ID. The focus is on enforcing Conditional Access (CA) policies to protect organizational resources from unauthorized access and identity-based threats.
By configuring and testing both Multi-Factor Authentication (MFA) and location-based access controls, this project highlights how organizations can mitigate risk, ensure compliance, and enforce least-privilege access in cloud environments.

-----

##  What This Project Covers

- Setting up **Global Secure Access** in Microsoft Entra
- Creating a **Named Location** using GPS-based country selection
- Applying **Conditional Access** to specific users or groups
- Blocking risky sign-ins from untrusted locations
- Requiring **MFA** and **compliant devices** for access

----

  ##  Tools Used

- Microsoft Entra ID (entra.microsoft.com)
- Microsoft 365 Admin Center (admin.microsoft.com)
  
------

##  Step-by-Step Guide


### Step 1: Set Up Global Secure Access

Before we get started, we need to turn on Global Secure Access for our tenant.
To do this, you’ll need one of these roles:

🔹 Global Administrator  
🔹 Conditional Access Administrator  
🔹 Global Secure Access Administrator

##### You can assign any of these roles from either the Entra Admin portal or the Microsoft 365 Admin center.
##### Once you have the role assigned, go back to the Entra Admin portal. On the left-hand pane, click on Global Secure Access > Settings > Session Management. 

##### Heads up: If you don’t see “Global Secure Access” right away after assigning the role, don’t worry. It might take a few minutes to show up due to propagation. Just refresh the page a few times and it should appear.

<img width="259" height="514" alt="image" src="https://github.com/user-attachments/assets/028e3900-b272-4d50-a2ed-3e221523f3ca" />

##### Here, click on activate, this may take some seconds or minutes.

<img width="975" height="529" alt="image" src="https://github.com/user-attachments/assets/804732c1-9747-42d3-9966-540aebae2fca" />

<img width="975" height="343" alt="image" src="https://github.com/user-attachments/assets/5dd5ad64-7712-455b-9f0a-d5d59340ffdd" />

<img width="975" height="199" alt="image" src="https://github.com/user-attachments/assets/3e90a848-b2ee-4569-98e8-dda634d2dfd7" />

##### Now go ahead and refresh the page or just click on Session Management again on the left side to refresh things. Once it loads properly, you should see Universal Tenant Restrictions and Adaptive Access.
##### Click on Adaptive Access, and make sure that the switch for "Enable Tenant Restrictions for Entra ID (Covering all cloud apps)" is toggled on.


<img width="975" height="357" alt="image" src="https://github.com/user-attachments/assets/bbcf2813-73ff-4099-90c5-5c576b389f97" />

<img width="975" height="494" alt="image" src="https://github.com/user-attachments/assets/aebdd246-1608-4e19-9b24-d5d1be64cbef" />

### Step 2: Create a Custom Named Location
- Before we create our policy, let’s first set up a custom Named Location based on our organization needs.
- Go to Identity Portal. You can get there from the Microsoft 365 Admin portal or just head straight to entra.microsoft.com.

  <img width="335" height="993" alt="image" src="https://github.com/user-attachments/assets/77f53399-faaa-4ee0-afe8-9e0431dd9434" />

  ##### Sign in using the admin credentials > Click on conditional access from the left options pane.

  <img width="405" height="1247" alt="image" src="https://github.com/user-attachments/assets/5d9804e2-3f19-46c3-ab28-b4f787a04f2d" />

- We create a custom Named Location first so we can apply it to the policy. This helps ensure remote or multi-location users aren’t accidentally blocked from accessing company resources. 
- To do this, go to: Conditional Access > Named Locations
- Then choose either Countries location or IP ranges location, depending on how you want to define the location (by country or by IP address range).

 <img width="975" height="692" alt="image" src="https://github.com/user-attachments/assets/040026bf-6706-488a-8311-df528f801d26" />

- I’m going with the first option, so I will go ahead and click on Countries Location.
- Give your Named Location a custom name, then choose "Determine location by GPS coordinate".
- Next, check the boxes for all the countries or locations you want to include, and then click Select.

  <img width="975" height="532" alt="image" src="https://github.com/user-attachments/assets/6cedcf4e-30fd-4f74-90f9-311cd65e197b" />

- Give it some time to propagate, then you should see your custom location populate. If not, click on the refresh icon on the page
 
 <img width="975" height="245" alt="image" src="https://github.com/user-attachments/assets/2c368b46-e757-4f6a-be36-f5ede13903ac" />

### Step 3: Create the Policy
Now let’s go ahead and create our policy.
From your current page, just click on Policies to get started.

<img width="975" height="921" alt="image" src="https://github.com/user-attachments/assets/ba167492-be6c-4231-9f28-1e38b7d5dbb7" />

##### Here you can decide to create a custom policy by clicking on the icon marked 1 or click on the icon marked as 2 to use the readily available template created by Microsoft

<img width="975" height="354" alt="image" src="https://github.com/user-attachments/assets/ef16c284-5642-498e-a806-15f8663e7e46" />

- Give your policy a name, then click on Specific Users Included to choose which users or groups you want to include or exclude. 
- Once you do that, the Include and Exclude options will show up on the right side.


<img width="975" height="636" alt="image" src="https://github.com/user-attachments/assets/407edf3c-e8c5-4cb8-9a60-9fe2abb2d9ff" />

<img width="975" height="636" alt="image" src="https://github.com/user-attachments/assets/7a61ad2f-ee08-4feb-9fc0-359ce8a766d0" />

##### I already have some test accounts I want to include in this policy, so I just check the boxes next to those accounts and click Select.

<img width="975" height="885" alt="image" src="https://github.com/user-attachments/assets/1f9043f0-5efa-403f-abcf-ef1d8a5265c2" />

- Next, choose which resources the policy should apply to by clicking on Target resources > then select Resources (formerly Cloud Apps).
- Pick the resources you want to include or exclude, but be careful not to lock yourself out, unless someone else has similar or higher permissions to access your org’s resources.

<img width="975" height="712" alt="image" src="https://github.com/user-attachments/assets/4c970ecd-4b9c-4932-bf2a-485a75caf2a4" />


- Now go to Network, toggle Yes to turn on the configuration, then click Select Networks and Locations.
- Choose the custom location we set up earlier, then click Save.

<img width="975" height="1008" alt="image" src="https://github.com/user-attachments/assets/11f1f727-9ed1-4373-a3be-8ceeb09d450a" />

<img width="975" height="519" alt="image" src="https://github.com/user-attachments/assets/97bcc403-3e83-4786-aa3b-02671de7f8e1" />

##### Let’s move to the Conditions Section, we should see that the custom location has been selected automatically. 

<img width="954" height="686" alt="image" src="https://github.com/user-attachments/assets/193a0977-8dcc-4c5d-b34a-c61c79ae5aea" />

- You can also set the policy to apply only to certain device platforms. For example, you can allow access only from authorized devices like Windows or macOS, and block access from mobile phones.
#### Feel free to explore other settings in the Conditions section based on what your organization needs.

<img width="975" height="482" alt="image" src="https://github.com/user-attachments/assets/dea7091f-0785-435f-9641-17779f6faef3" />


### Step 4: Set the Policy Action

- Now we need to tell the policy what action to take, either to block access or grant access.
- Since this is for our remote workers in a different region, I’ll go with Grant Access, but I’ll also require them to do extra authentication by selecting Require MFA.
- I also want to make sure they’re signing in from a compliant device, so I’ll check that option too.

  <img width="975" height="538" alt="image" src="https://github.com/user-attachments/assets/4c2cab49-eb9e-4c50-98ba-f2828d56eb73" />


##### Click Save, make sure the policy is toggled On, then click Create.
##### After that, refresh the page so the changes will propagate accordingly

<img width="878" height="1350" alt="image" src="https://github.com/user-attachments/assets/c193bc7e-b6e7-41dc-9f57-992190d3585a" />

##### We have now successfully created a location-based access policy for our remote workers. The status of the policy should be On. If yours isn’t, then you need to retrace your steps to ensure that you actually enabled the policy. 

<img width="975" height="406" alt="image" src="https://github.com/user-attachments/assets/1abd5acd-1993-480f-b3b2-9216baf3dbd7" />

## Alternate Option
If the reverse were to be the case and we want to block users from signing in from these risky locations. Then we create a custom Named Location and include all the risky countries we don’t want users signing in from. 

<img width="975" height="254" alt="image" src="https://github.com/user-attachments/assets/27ccc17e-947e-407a-a060-25de7b8e0c3b" />

### Step 1: Create the Policy
Now let’s proceed to create a Policy to reflect this action. I have specified the Group I want this policy applied to. You can choose to exclude certain users or groups depending on your organization requirements or needs. 

<img width="975" height="918" alt="image" src="https://github.com/user-attachments/assets/f039b97e-52f4-4f79-85a0-1a94eb01e299" />


### Step 2: Set the Target Resource and Network
- Now repeat the same step previously carried out for the Target resource.
- For the Network section, select the custom Named Location we created in Step 1 (called Blocked Risky Locations), and make sure to exclude the trusted location already set up in your tenant.
- Also, don’t forget to toggle the Configure button to Yes.


<img width="975" height="783" alt="image" src="https://github.com/user-attachments/assets/0996c45d-7908-419e-aa1b-d8da8ae5a352" />


<img width="975" height="389" alt="image" src="https://github.com/user-attachments/assets/b864d4b2-7277-4a3d-aa2a-3a19f8026fd5" />

<img width="975" height="802" alt="image" src="https://github.com/user-attachments/assets/6fd95085-0fcb-4677-bb4b-85681bcab8d0" />

- The settings should automatically reflect under the Conditions section.
- Now let’s move to the Grant section. Here, choose Block Access, then click Select.
- Make sure the Enable Policy toggle is set to Yes, then click Create.
- Finally, refresh the page and your policy should populate.


<img width="523" height="667" alt="image" src="https://github.com/user-attachments/assets/39738cc7-138b-4810-8eb4-f4ed68da7911" />


<img width="634" height="523" alt="image" src="https://github.com/user-attachments/assets/6a5852ef-4305-4e20-ba86-b9e46f44a35c" />

## Results

### Result 1

- It is highly recommended to test your policy before rolling it out fully to make sure everything works as expected.
- I tried accessing the organization’s resources using one of the test accounts included in the initial setup, and here’s the result I got (based on the Location and MFA based Policy):

<img width="975" height="752" alt="image" src="https://github.com/user-attachments/assets/66dd3fc4-cb67-449c-8796-f99b0f688fb2" />

##### Note: Prior to enabling the policy, I could access the Customer Support account without MFA, since I hadn’t set it up yet.
-  Once the policy was active, I was prompted to set up MFA. After approving the sign-in through the Authenticator app, I was also prompted to share my location.
- This confirms that the policy is working as expected. If the shared location doesn’t match the allowed locations in the policy, access will be blocked/denied.

<img width="975" height="1121" alt="image" src="https://github.com/user-attachments/assets/618b0c1c-7a30-4f35-9da9-7e59f090cfec" />

<img width="975" height="810" alt="image" src="https://github.com/user-attachments/assets/801c06a4-e018-4962-abee-5ffb62296f97" />


### Result 2
I tried accessing the organization’s resources from one of the restricted regions and my access was denied (Based on the Blocked Risky Location Policy)

<img width="908" height="917" alt="image" src="https://github.com/user-attachments/assets/aeb56bd9-4950-48d4-9e25-4e1201cb5ed1" />

<img width="975" height="603" alt="image" src="https://github.com/user-attachments/assets/6abac85a-4aec-4ca1-8b09-c8e70cded077" />


### Summary of Results
- Users from risky or blocked locations are denied access
- Remote users from trusted regions must use MFA and compliant devices
- Policies reflect Zero Trust principles: "Never trust, always verify"


##  Security Concepts Demonstrated

This project demonstrates the application of Zero Trust architecture by implementing Conditional Access policies in Microsoft Entra ID. It includes configuring Named Locations and network-based access controls to manage how and where users can access organizational resources. To strengthen security, Multi-Factor Authentication (MFA) is enforced for remote users, ensuring that only trusted users on compliant devices can sign in from approved locations.


##  Got any Questions?

Feel free to reach out! I will be glad to answer your questions. 

### I hope you found this lab as interesting as I did. Thank you for reading this far. 
 


 









