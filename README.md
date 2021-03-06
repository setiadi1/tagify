Tagify - lightweight input "tags" script
========

<!--
```
<custom-element-demo>
  <template>
    <script src="https://yaireo.github.io/tagify/dist/tagify.js"></script>
    <script src="https://yaireo.github.io/tagify/dist/tagify.css"></script>
    <input name='tags' placeholder='write some tags' value='css, html, javascript, css'>
  </template>
</custom-element-demo>
```
-->

![alt tag](https://raw.githubusercontent.com/yairEO/tagify/master/demo.gif)

Want to simply convert an input field into a tags element, in a easy customizable way,
with good performance and smallest code footprint? You are in the right place my friend.

##[Demo page](https://yaireo.github.io/tagify/)

### Selling points
* supports whitelist (with native suggestions dropdown as-you-type)
* supports blacklists
* JS file is under 150 very readiable lines of code
* JS weights less than ~5kb
* SCSS file is ~2kb of highly readable and flexible code
* No other inputs are used beside the original, and its value is kept in sync
* Can paste in multiple values ("tag 1, tag 2, tag 3")
* Automatically disallow duplicate tags (vis "settings" object)
* Tags can be created by commas *or* by pressing the "Enter" key
* Tags can be trimmed via `hellip` by giving `max-width` to the `tag` element in your `CSS`
* Easily customized


### building the project
Simply run `gulp` in your terminal, from the project's path.


### Basic usage
Lets say this is your markup, and you already have a value set on the input (which was pre-filled by data from the server):

```html
<input name='tags' placeholder='write some tags' value='foo, bar,buzz'>
<textarea name='tags' placeholder='write some tags'>foo, bar,buzz</textarea>
```

what you need to do to convert that nice input into "tags" is simply select your input/textarea and run `tagify()`:

```javascript
// vanilla component
var input = document.querySelector('input[name=tags]'),
    tagify = new Tagify( input );

// with settings passed
tagify = new Tagify( input, {duplicates:true, whitelist:['foo', 'bar']} );

// when using jQuery plugin version file `jQuery.tagify.js`
$('[name=tags]').tagify()
```

Now markup be like:

```html
<tags>
    <tag>
        <x></x>
        <div><span title="css">css</span></div>
    </tag>
    <tag>
        <x></x>
        <div><span title="html">html</span></div>
    </tag>
    <tag>
        <x></x>
        <div><span title="javascript">javascript</span></div>
    </tag>
    <div>
        <input list="tagsSuggestions3l9nbieyr" class="input placeholder">
        <datalist id="tagsSuggestions3l9nbieyr">
            <label> select from the list:
                <select>
                    <option value=""></option>
                    <option>foo</option>
                    <option>bar</option>
                </select>
            </label>
        </datalist><span>write some tags</span>
    </div>
    <input name="tags" placeholder="write some tags" value="foo, bar,buzz">
</tags>
```

### Settings

Name            | Type       | Default     | Info
--------------- | ---------- | ----------- | --------------------------------------------------------------------------
duplicates      | Boolean    | false       | (flag) should duplicate tags be allowed or not
enforeWhitelist | Boolean    | false       | should ONLY use tags allowed in whitelist
autocomplete    | Boolean    | true        | show native suggeestions list, as you type
whitelist       | Array      | []          | an array of tags which only they are allowed
blacklist       | Array      | []          | an array of tags which aren't allowed


