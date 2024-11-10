# Identify integrator activity

To help integrators track and identify activity originating from their applications, Snapshot supports an optional `app` parameter. This parameter can be included when users cast votes or create proposals, allowing you to tag these actions with your application's identifier.

### **Using `app` with Snapshot.js**

If you're integrating Snapshot's voting and proposal functionalities directly into your platform using [Snapshot.js](https://github.com/snapshot-labs/snapshot.js), you can include the `app` parameter in your function calls:

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();

const receipt = await client.vote(web3, account, {
  space: 'yam.eth',
  proposal: '0x21ea31e896ec5b5a49a3653e51e787ee834aaf953263144ab936ed756f36609f',
  type: 'single-choice',
  choice: 1,
  reason: 'Choice 1 makes a lot of sense',
  app: 'yourappname'
});
```

### **Adding `app` to Snapshot URLs**

For platforms that redirect users to Snapshot, you can append the `app` parameter to the URL. This tags the action with your application's identifier when the user interacts on Snapshot.

**URL format:**

```
https://snapshot.box/#/{network}:{space}/proposal/{proposalId}?app={yourappname}
```

**Example:**

```
https://snapshot.box/#/s:ens.eth/proposal/0xfa54ff2b55f0495c96ec2d8645241bcff48ca6afe1f4925fb51f29c4667252df?app=boardroom
```

**Parameter requirements**

* **Format:** Lowercase alphanumeric string
* **Maximum length:** 24 characters
* **Purpose:** The `app` parameter will be stored with the vote or proposal data on Snapshot. This enables you to identify and analyze activities originating from your application.

By using the `app` parameter, you can seamlessly integrate Snapshot into your platform while maintaining clear visibility over user interactions related to your application.
