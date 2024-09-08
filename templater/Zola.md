<%*
let title = this.app.workspace.getActiveFile().basename
if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Title") ?? "Untitled";
    newTitle = tp.date.now() + "-" + `${title.replace(/\s+/g, '-').toLowerCase()}`;
    await tp.file.rename(newTitle);
}
-%>
---
title: <% title %>
date: <% tp.date.now() %>
taxonomies:
  tags: []
---
