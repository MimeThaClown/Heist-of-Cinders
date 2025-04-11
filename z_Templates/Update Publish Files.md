```
<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;


const fileAndQuery = new Map([
  [
	  "Heist of Cinders",
	  'TABLE WITHOUT ID player AS "Player", name AS "Name",class AS "Class", race AS "Race", 3 AS "Lev```


el" FROM "CharacterInfo/C1" SORT name ASC',
	],
  
  
]);


await fileAndQuery.forEach(async (query, filename) => {
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }
  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent = `%% #Ignore update via "Update Publish Files" template %% \n\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
openPublishPanel();
%>

