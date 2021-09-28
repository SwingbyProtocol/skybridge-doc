# Add amount or extends lock period into an existing locked transaction

### 1. Relock existing timelock in [Timelock portal](https://timelock.swingby.network/)

1. Click the "relock" button on the existing timelock transaction. 

{% hint style="warning" %}
**DO NOT**  click "Add New Timelock" if you want to add an amount or extends the lock period.
{% endhint %}

![](../../.gitbook/assets/image%20%289%29.png)

2. Update the amount or lock period and click "Relock"

![](../../.gitbook/assets/image%20%2816%29.png)

3. Now you can see the updated timelock transaction.

![](../../.gitbook/assets/image%20%2819%29.png)



### 2. Update locked amount into the Skybridge contract

{% hint style="warning" %}
You may skip this step if you are only extending the period of the existing timelock.
{% endhint %}

Skybridge refers to the latest locked amount by contract when distributing sbBTC.

Use the Telegram bot to take your node offline and update the latest amount of data into Skybridge contract. Bring the node online again once the churn transaction has been updated.

1. Process the `/stop_node` command into the Telegram bot after you have relocked in the Timelock portal.

2. Note down the `last churning transaction hash` show on the [Metanodes page](https://skybridge.info/metanodes?bridge=btc_erc).

![](../../.gitbook/assets/image%20%2838%29.png)

3. Process the `/deploy_node` command once `last churning transaction` has been updated in step 2.

That's all! 

![](../../.gitbook/assets/image%20%2837%29.png)

{% hint style="info" %}
[Metanodes page](https://skybridge.info/metanodes?bridge=btc_erc) updated nodes status periodically using cached data. It takes few hours ~ 1 day to update the node's status. 
{% endhint %}

{% hint style="danger" %}
To avoid missing receive SWINGBY rewards, **MAKE SURE** your node is online at least by 9AM UTC Saturday. Your node can be brought back online any time by processing the`/deploy_node` command in the Telegram bot.
{% endhint %}

{% hint style="success" %}
Swingby will deploy the new contract with a major upgrade in the future. The upgraded contract will update the locked amount into the contract automatically without going through steps 1~3 in the Telegram bot.
{% endhint %}

