# generator-ego-samples :: git

## [downloadGitRepo()](https://github.com/egodigital/generator-ego/wiki#downloadgitreporepo-dest-opts-)

Create a `yo-ego.js` file inside your home directory, if needed, and add an entry like that:

```json
exports.generators = {
    'downloadGitRepo() test': 'downloadGitRepo_test.js'
};
```

Now create a `downloadGitRepo_test.js` file in the same directory and fill it with the following content:

```javascript
exports.run = async function() {
    const NAME_AND_TITLE = await this.tools
        .askForNameAndTitle();
    if (!NAME_AND_TITLE) {
        return;
    }

    const OUT_DIR = NAME_AND_TITLE.mkDestinationDir();

    // this will download the repository from
    // 'https://github.com/egodigital/vscode-powertools'
    // to the target directory
    await this.tools.downloadGitRepo(
        'https://github.com/egodigital/vscode-powertools',
        OUT_DIR
    );

    // ask for (new) Git repository
    await this.tools
        .askForGitInit(OUT_DIR);

    // ask for open Visual Studio Code
    await this.tools
        .askForOpenVSCode(OUT_DIR);
```

Now start with `yo ego` and select `downloadGitRepo() test`.
