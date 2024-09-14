<%*
const {app, moment} = this;
const file = app.workspace.getActiveFile();
const frontmatter = app.metadataCache.getFileCache(file).frontmatter;

if (frontmatter && frontmatter.title) {
    const newTitle = `${moment(file.basename, "YYYY-MM-DD").format("YYYY-MM-DD")}-${frontmatter.title.toLowerCase().replace(/ /g, "-")}`;
    await app.fileManager.renameFile(file, `${file.parent.path}/${newTitle}.md`);
}
%>

