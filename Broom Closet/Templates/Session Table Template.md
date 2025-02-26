```
// Update Publish Files.md
<%*
const dv = app.plugins.plugins["dataview"].api;
const filename = "Testing";
const query = `TABLE WITHOUT ID
file.link AS Session, file.ctime AS Date
FROM "Session Archive"
SORT file.Ctime desc
LIMIT 25`;

const tFile = tp.file.find_tfile(filename);
const queryOutput = await dv.queryMarkdown(query);

// write query output to file
await app.vault.modify(tFile, queryOutput.value);
%>
```