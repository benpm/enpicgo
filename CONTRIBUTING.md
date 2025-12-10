## Contribution Guidelines

### Installation and Startup

1. Use [yarn](https://yarnpkg.com/) to install dependencies

```bash
yarn install
```

Then run

```bash
yarn dev
```

to start the project.

2. Please add code only related to the main process of Electron in the `src/main` directory. Code only related to the rendering process should be added in the `src/renderer` directory. Add code that can be used by both processes in the `src/universal` directory. **Note**: The rendering process does not have `Node.js` capability. All rendering processes that need to use `Node.js` modules should add events under `src/main/events/picgoCoreIPC.ts` for processing.

3. All cross-process event names should be added in `src/universal/events/constants.ts`.

4. All global type definitions should be added in `src/universal/types/`. If it is an `enum`, please add it in `src/universal/types/enum.ts`.


### i18n

1. Create a language `yml` file under `public/i18n/`, for example `zh-Hans.yml`. Then refer to `zh-CN.yml` or `en.yml` to write the language file. Note that PicGo will display the language name to users through the `LANG_DISPLAY_LABEL` in the language file.

2. Add a default language in `src/universal/i18n/index.ts`. The `label` is the value of `LANG_DISPLAY_LABEL` in the language file, and `value` is the language file name.

3. If you are updating an existing language file, please run `yarn gen-i18n` after the update to ensure the correct language definition file is generated.

### Submit Code

1. Please check that the code does not have extra comments, `console.log`, or other debugging code.
2. Before submitting code, please execute the command `git add . && yarn cz` to invoke PicGo's [code submission standard tool](https://github.com/PicGo/bump-version). Submit code through this tool.
