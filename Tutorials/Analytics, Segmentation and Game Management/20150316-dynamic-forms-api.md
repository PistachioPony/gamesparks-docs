
# Dynamic Forms API

In addition to regular HTML you are able to use Game Sparks Markup Language (GSML) which is based on HTML and was created for the purposes of Dynamic Forms. GSML allows ease of use and rapid Dynamic Form development, what would otherwise require complex HTML structures is essentially shrunk down to a few lines of code. [su_tabs] [su_tab title="gs-row"] gs-row is a HTML row container, by default it's set to width of 12. Note: gs-rows and gs-cols can be nested to create your preferred layout.

#### Options

gs-row takes no additional options.

#### Example

```    
    <gs-row>
        Your content here.
    </gs-row>
```

[/su_tab] [su_tab title="gs-col"] gs-col is a HTML column. Note: gs-rows and gs-cols can be nested to create your preferred layout.

#### Options

*width* \- is the width of the column, this can be between 1 and 12. If not defined, the width will be 12. *align* \- is the alignment of the content within the column (left, right). If not defined, the content will be centered.

#### Example

```    
    <gs-col width="6" align="left">
        Your content here.
    </gs-col>
```

[/su_tab] [su_tab title="gs-title-block"] gs-title-block is a title block styled to match the rest of Gamesparks portal styling.

#### Options

*padding* - is the padding of the title block. If not defined, the padding will be 0. *margin* \- is the margin of the title block. If not defined, the margin will be 0. *title* \- the title of the title block. *height* \- height of the title block. When defined, any content outside of the bounds, will make the title block scrollable. *width* \- the width of the title block, this can be between 1 and 12. If not defined, the width will be 12.

#### Example

```    
    <gs-title-block padding="5" margin="1" title="Title Block" height="40" width="6">
        Your content here.
    </gs-title-block>
```

#### Output

![gs-title-block-output](/wp-content/uploads/2015/01/gs-title-block-output.jpg)

 [/su_tab] [su_tab title="gs-placeholder"] gs-placeholder is a placeholder within a form, this placeholder can be dynamically updated on the fly by targeting it with links, forms and snippets.

#### Options

*id* \- id should be a unique identifier, this identifier allows links, forms and snippets to locate and overwrite the placeholder.

#### Example

```    
    <gs-placeholder id="unique__placeholder">
        Your initial content here.
    </gs-placeholder>
```

[/su_tab] [su_tab title="gs-form"] gs-form is a HTML form that can be submitted to a snippet, passing in some input data.

#### Options

*snippet* \- a snippet shortcode to call with the input values. Additionally you can also append values directly here. *target* \- this is the id of a placeholder, where the output of the snippet will be placed.

#### Example

```
    <gs-form snippet="snippet_shortcode?update=true&upsert=false" target="unique__placeholder">
        <gs-row>
            <gs-col width="2">
                <input type="number" min="1" max="10" name="rank" value="5"/>
            </gs-col>
            <gs-col width="4">
                <input type="text" placeholder="Player/Team ID" name="playerId" value=""/>
            </gs-col>
            <gs-col width="2">
                <gs-submit>Submit</gs-submit>
            </gs-col>
        </gs-row>    
    </gs-form>
```

#### Output

![gs-form-output](/wp-content/uploads/2015/01/gs-form-output.jpg) Clicking *Submit* in this form will:

  * Call a snippet with shortcode: *snippet_shortcode*
  * Pass in parameters: *update* = true, *upsert* = false, *rank* = (your number), *playerId* = (your text)
  * And render the snippets output at a placeholder with Id: *unique__placeholder*
[/su_tab] [su_tab title="gs-submit"] gs-submit is a custom form submit button, the functionality behind gs-submit allows you to override where the form is going to be submitted to or where the output will be rendered at.

#### Options

* *snippet* \- this is an optional snippet shortcode, which allows the submit button override the snippet where the form is supposed to be submitted to.
* *target* \- this is an optional placeholder id, which allows the submit button override the placeholder where the output is supposed to be rendered at.

#### Example

```
    <gs-form snippet="snippet_shortcode" target="unique__placeholder">
        <gs-row>
            <gs-col width="2">
                <gs-submit>Submit</gs-submit>
            </gs-col>
            <gs-col width="1">
                <gs-submit snippet="another_shortcode?plus=true" target="another__placeholder">
                    <i class="icon-plus"></i>
                </gs-submit>
            </gs-col>
        </gs-row>
    </gs-form>
```

#### Output

![gs-submit-output](/wp-content/uploads/2015/01/gs-submit-output.jpg) By clicking *Submit *button, you will submit the form to the snippet with shortcode: *snippet_shortcode *and render the output at the placeholder Id: *unique__placeholder*. By clicking the *Plus* icon, you will submit the form to the snippet with shortcode : *another_shortcode *and render the output at the placeholder Id: *another__placeholder*, additionally you will submit a parameter to the snippet *plus* = true. [/su_tab] [su_tab title="gs-link"] gs-link is a HTML link that can execute a snippet upon clicking it.

#### Options

*snippet* - a snippet shortcode to execute, you can append parameters directly here. *target* - this is the id of a placeholder, where the output of the snippet will be placed.

#### Example


    <gs-link snippet="snippet_shortcode?fromLink=true" target="unique__placeholder">Click me!</gs-link>

Clicking this link will execute a snippet with shortcode: *snippet_shortcode *passing in a parameter *fromLink *= true and render the output at the placeholder with the Id: *unique__placeholder*. [/su_tab] [su_tab title="gs-alert"] gs-alert is useful for displaying simple alerts.

#### Options

* *type* \- type of the message to display, these can be success, warn and error.
* *message* \- message to display.

#### Example

```
    <gs-row>
        <gs-col width="4">
            <gs-alert type="success" message="Success!"></gs-alert>
        </gs-col>
        <gs-col width="4">
            <gs-alert type="warn" message="Warning!"></gs-alert>
        </gs-col>
        <gs-col width="4">
            <gs-alert type="error" message="Error!"></gs-alert>
        </gs-col>
    </gs-row>
```

#### Output

![gs-alert-output](/wp-content/uploads/2015/01/gs-alert-output.jpg) [/su_tab] [su_tab title="gs-snippet"]
