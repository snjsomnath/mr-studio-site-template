Your own code layers, one folder each, for what the core layers and the editor's layer builder
can't do. Make one with `mrstudio layer new . <id>` and build them with `mrstudio layer build .`;
the app loads the built `dist/index.js`. See docs/contracts/layer.md, Site layers, in the
MR Studio repository. Most tables need none: try **Add › New layer** and **Add › Custom layer** in the editor first.
