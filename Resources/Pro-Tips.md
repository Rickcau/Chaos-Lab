az graph query -q "ChaosResources | where type == 'microsoft.chaos/targets/capabilities' | where subscriptionId == 'mySubscriptionID'"
