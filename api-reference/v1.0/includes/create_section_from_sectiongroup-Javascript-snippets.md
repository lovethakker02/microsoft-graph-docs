
```Javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onenoteSection = {
  displayName: "Section name"
};

let res = await client.api('/me/onenote/sectionGroups/{id}/sections')
	.post({onenoteSection : onenoteSection});

```