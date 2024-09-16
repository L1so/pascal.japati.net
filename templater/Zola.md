<%*
let title = this.app.workspace.getActiveFile().basename;

if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Title") ?? "Untitled";
    newTitle = tp.date.now() + "-" + `${title.replace(/\s+/g, '-').toLowerCase()}`;
    let newFolderPath = `/content/${newTitle}`; // Update to your desired base path
    try {
        await this.app.vault.createFolder(newFolderPath);
    } catch (error) {
        // Catch error if the folder already exists
        console.log("Folder already exists or could not be created: ", error);
    }
    await tp.file.move(`${newFolderPath}/index`);
}
-%>
---
title: <% title %>
date: <% tp.date.now() %>
taxonomies:
  tags: []
---
