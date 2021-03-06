---
title: Tutorial - Reduce Azure costs with optimization recommendations | Microsoft Docs
description: This tutorial helps you reduce Azure costs when you act on optimization recommendations.
services: cost-management
keywords:
author: bandersmsft
ms.author: banders
ms.date: 09/10/2018
ms.topic: conceptual
ms.service: cost-management
manager: dougeby
ms.custom:
---

# Tutorial: Optimize costs from recommendations

Azure Cost Management works with Azure Advisor to provide cost optimization recommendations. Azure Advisor helps you optimize and improve efficiency by identifying idle and underutilized resources. This tutorial walks you through an example where you identify underutilized Azure resources and then you take action to reduce costs.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * View cost optimization recommendations to view potential usage inefficiencies
> * Act on a recommendation to resize a virtual machine to a more cost-effective option
> * Verify the action to ensure that the virtual machine was successfully resized

## Prerequisites
You must have an [Azure Enterprise Agreement (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/) with at least read access to one or more of the following items:

- Azure EA subscription
- Azure EA subscription resource group

And you must have active virtual machines with at least 14 days of activity.

## Sign in to Azure
Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com/).

## View cost optimization recommendations

In the Azure portal, click **Cost Management + Billing** in the list of services. Then in the list under **Cost Management**, select **Advisor Recommendations**. Advisor Cost recommendations are shown.

![Advisor recommendations](./media/tutorial-acm-opt-recommendations/advisor-recommendations.png)

The list of recommendations identifies usage inefficiencies or shows purchase recommendations that can help you save additional money.

The **Impact** setting, along with the **potential monthly savings**, are designed to help identify recommendations that have the potential to save as much as possible. High impact recommendations are [Buy reserved virtual machine instances to save money over pay-as-you-go costs](../advisor/advisor-cost-recommendations.md#buy-reserved-virtual-machine-instances-to-save-money-over-pay-as-you-go-costs) and [Optimize virtual machine spend by resizing or shutting down underutilized instances](../advisor/advisor-cost-recommendations.md#optimize-virtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances). Medium impact recommendations are [Reduce costs by eliminating un-provisioned ExpressRoute circuits](../advisor/advisor-cost-recommendations.md#reduce-costs-by-eliminating-unprovisioned-expressroute-circuits) and [Reduce costs by deleting or reconfiguring idle virtual network gateways](../advisor/advisor-cost-recommendations.md#reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways).

## Act on a recommendation

Azure Advisor monitors your virtual machine usage for 14 days and then identifies underutilized virtual machines. Virtual machines whose CPU utilization is five percent or less and network usage is seven MB or less for four or more days are considered low-utilization virtual machines.

The 5% or less CPU utilization setting is the default, but you can adjust the settings. For more information about adjusting the setting, see the [Configure the average CPU utilization rule](../advisor/advisor-get-started.md#configure-the-average-cpu-utilization-rule-for-the-low-usage-virtual-machine-recommendation) article [for the low usage virtual machine recommendation](../advisor/advisor-get-started.md#configure-the-average-cpu-utilization-rule-for-the-low-usage-virtual-machine-recommendation).

Although some scenarios can result in low utilization by design, you can often save money by changing the size of your virtual machines to less expensive sizes.

You can save up to the amount shown if you shut down or deallocate the virtual machine. However, your actual savings might vary if you choose a resize action. Let's walk through an example of resizing a virtual machine.

In the list of recommendations, click the **Right-size or shutdown underutilized virtual machines** recommendation. In the list of virtual machine candidates, choose a virtual machine to resize and then click the virtual machine. The virtual machine's details are shown so that you can verify the utilization metrics.

![Recommendation details](./media/tutorial-acm-opt-recommendations/recommendation-details.png)

In the VM details, check the utilization of the virtual machine to confirm that it's a suitable resize candidate.

![VM details](./media/tutorial-acm-opt-recommendations/vm-details.png)

Note the current virtual machine's size. After you've verified that the virtual machine should be resized, close the VM details so that you see the list of virtual machines.

In the list of candidates to shut down or resize, select **Resize the virtual machine**.
![Resize the virtual machine](./media/tutorial-acm-opt-recommendations/resize-vm.png)

Next, you're presented with a list of available resize options. Choose the one that will give the best performance and cost-effectiveness for your scenario. In the following example, the option chosen resizes from a **DS14\_V2** to a **DS13\_V2**. Following the recommendation saves $551.30/month.

![Choose a size](./media/tutorial-acm-opt-recommendations/choose-size.png)

After you choose a suitable size, click **Select** to start the resize action.

Resizing requires an actively running virtual machine to restart. If the virtual machine is in a production environment, we recommend that you run the resize operation after business hours. Scheduling the restart can reduce disruptions caused by momentarily unavailability.

## Verify the action

When the VM resizing completes successfully, an Azure notification is shown.

![Resized notification](./media/tutorial-acm-opt-recommendations/resized-notification.png)

## Next steps

In this tutorial, you learned how to:

> [!div class="checklist"]
> * View cost optimization recommendations to view potential usage inefficiencies
> * Act on a recommendation to resize a virtual machine to a more cost-effective option
> * Verify the action to ensure that the virtual machine was successfully resized

If you haven't already read the Cost Management best practices article, it provides high-level guidance and principles to consider to help manage costs.

> [!div class="nextstepaction"]
> [Cost Management best practices](cost-mgt-best-practices.md)
