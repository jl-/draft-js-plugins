# DraftJS Plugins

![Draft JS Plugins Logo](https://dl.dropboxusercontent.com/u/40735/draft-js-plugins.svg)

High quality plugins with great UX on top of [DraftJS](https://github.com/facebook/draft-js).

## Available Plugins

- [Emoji](https://www.draft-js-plugins.com/plugin/emoji)
- [Stickers](https://www.draft-js-plugins.com/plugin/sticker)
- [Hashtags](https://www.draft-js-plugins.com/plugin/hashtag)
- [Linkify](https://www.draft-js-plugins.com/plugin/linkify)
- [Mentions](https://www.draft-js-plugins.com/plugin/mention)
- [Undo](https://www.draft-js-plugins.com/plugin/undo)
- or build your own … :)

[![Build Status](https://travis-ci.org/draft-js-plugins/draft-js-plugins.svg?branch=master)](https://travis-ci.org/draft-js-plugins/draft-js-plugins)

## Live Example & Documentation

Checkout [the website](https://www.draft-js-plugins.com/)!

## Usage

First, install the editor with `npm`:

```
$ npm install draft-js-plugins-editor --save
```

and then import it somewhere in your code and you're ready to go!

```js
import Editor from 'draft-js-plugins-editor';
```

## Documentation

### draft-js-plugins-editor

#### Editor

An editor component accepting plugins.

| Props                                          | Description  | Required
| -----------------------------------------------|:------------:| -------:|
| editorState                                    | [see here](https://facebook.github.io/draft-js/docs/api-reference-editor-state.html#content)| * |
| onChange                                       | [see here](https://facebook.github.io/draft-js/docs/api-reference-editor.html#onchange)| * |
| plugins                                        | an array of plugins |  |
| all other props accepted by the DraftJS Editor | [see here](https://facebook.github.io/draft-js/docs/api-reference-editor.html#props) |  |

Usage:

```js
import React, { Component } from 'react';
import Editor from 'draft-js-plugins-editor';
import createHashtagPlugin from 'draft-js-hashtag-plugin';
import createLinkifyPlugin from 'draft-js-linkify-plugin';
import { EditorState } from 'draft-js';

const hashtagPlugin = createHashtagPlugin();
const linkifyPlugin = createLinkifyPlugin();

const plugins = [
  hashtagPlugin,
  linkifyPlugin,
];

export default class UnicornEditor extends Component {

  state = {
    editorState: EditorState.createEmpty(),
  };

  onChange = (editorState) => {
    this.setState({
      editorState,
    });
  };

  render() {
    return (
      <Editor
        editorState={this.state.editorState}
        onChange={this.onChange}
        plugins={plugins}
        ref="editor"
      />
    );
  }
}
```

#### How to write a Plugin

Feel free to copy any of the existing plugins as a starting point. Feel free to directly contact [@nikgraf](https://github.com/nikgraf) in case you need help or open a Github Issue!

More documentation is coming soon…

## Discussion and Support
Join the channel #plugin-editor after signing into the DraftJS [Slack organization](https://draftjs.herokuapp.com)!

## Development

You must have [Node.js v5](https://nodejs.org/en/download/package-manager/) or later installed to develop DraftJS plugins.

```sh
npm install
cd docs
npm install
npm start
```

## Publishing Github Pages

Run `./script/publishGithubPages.sh`

The `build` script renames the .babelrc files of all plugins to avoid issues with the build. In the future we might be able to remove this again.

## License

MIT
