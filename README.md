# What to Do If You Shut Down Your Managed FortiGate NVA in Azure vWAN

When deploying a FortiGate Network Virtual Appliance (NVA) into a Virtual WAN hub, certain intricacies surround its management and operations, particularly when shutting down your managed NVA. In this article, we will walk you through the steps to get your NVA back up and running with Microsoft's assistance.

## Understanding the Scenario

When you execute an "exec shutdown", you send a guest OS shutdown signal to Azure. Due to the managed nature of this deployment, once the NVA is shut down, there's no direct method to power it back on using the Azure Portal or API.

## Understanding the Resource Groups

Upon deployment, two primary resource groups are established within a customer's subscription:

- **Customer resource group**: Serves as a placeholder for the managed application. Here, partners have the flexibility to define customer-specific attributes.

- **Managed resource group**: This group is more stringent. Overseen by the managed application's publisher, it  hosts the `FortiGate NVA` resources. Direct modifications by customers are disallowed in this zone.

## Navigating Permissions

The managed resource group comes with a protective layer - a default "deny-all" Azure Active Directory assignment. This safeguard:

- Prevents any write operations.
- Particularly safeguards the Network Virtual Appliance resources.

## Steps to Contact Microsoft for Assistance

If you find yourself in this situation, fret not. Here’s a step-by-step guide to getting your virtual machine restarted:

### 1. Prepare Your Details

Gather the necessary details about your Azure vWAN and NVA deployment. This helps Microsoft’s team locate and troubleshoot your specific resource faster.

Copy the Managed application **Id**, in addition to the **Managed Resource Group Id**.

> Customer Resource Group > Managed Application > Properties

![ManagedApplicationProperties](https://raw.githubusercontent.com/AJLab-GH/Azure-vWAN-FAQ/main/Images/vWAN-ID-Screenshot.png)

### 2. Access Microsoft's Support

Navigate to the Azure Portal's Help + support section. Once there, opt to create a new service request.

### 3. Fill out the Support Request Form

- **Issue Type:** Select "Technical".
- **Subscription:** Choose the Azure subscription associated with your vWAN NVA deployment.
- **Resource:** Even if you can’t directly access the NVA, providing its name or any related resources can be helpful.
- **Problem Type:** Opt for "Networking" and then "Virtual WAN" from the dropdown.
- **Description:** Clearly state that you've initiated a shutdown on the managed NVA and require assistance to restart it.

## Emailing Fortinet

Once you've completed the aforementioned steps, it’s essential to keep Fortinet in the loop. Send an email to: [azurevwan@fortinet.com](mailto:azurevwan@fortinet.com) with the Service Request Information from the Azure Service Request you opened in the previous Step.

The specific details required to contact the Fortinet can be located by navigating as directed:

> Customer Resource Group > Managed Application > Properties

![CxSupportInformation](https://raw.githubusercontent.com/AJLab-GH/Azure-vWAN-FAQ/main/Images/vWAN_Support_contact.png)

## Conclusion

The managed nature of NVA deployments in Azure vWAN offers several benefits, but it also means you rely more heavily on Microsoft for certain operations. By following the steps outlined above, you can ensure minimal downtime and maintain a seamless network operation.