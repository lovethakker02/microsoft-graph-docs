---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const personAnniversary = {
  type: "type-value",
  date: "datetime-value"
};

let res = await client.api('/me/profile/anniversaries/{id}')
	.version('beta')
	.update(personAnniversary);

```