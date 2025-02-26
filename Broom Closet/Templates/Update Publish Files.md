<%*
const dv = app.plugins.plugins["dataview"].api;
const fileAndQuery = new Map([
  [
    "Latest Sessions",
    'TABLE WITHOUT ID file.link AS Session, file.ctime AS Date FROM "Session Archive" SORT file.name desc LIMIT 7',
  ],
]);

for (let [filename, query] of fileAndQuery) {
  const tFile = tp.file.find_tfile(filename) || await tp.file.create_new("", filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent = `---\npublish: true\n---\n${queryOutput.value}`;
  await app.vault.modify(tFile, fileContent);
}
%>

