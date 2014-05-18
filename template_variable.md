---
layout: default
title: Template Variable
category: Documentation
weight: 1
---

All options for a custom template variable are set in a PHP Array or JSON config file in the folder *configs* with the same name as the template variable (otherwise the default config is used) and *.config.inc.php* or *config.json* as extension (a JSON file is used in priority to PHP Array file).

### Display mode

The display mode of the input fields in the multi field list could be set in the key `display` to *horizontal* (events example), *vertical* (images example), *single*, *datatable* (links or multicontent example) or *dbtable* (dbtabledemo example). A multiTV with single display configuration contains only one list element.

### Fields

The fields of the multitv could be defined in the key `fields`. This key contains an array of fieldnames and each fieldname contains an array of field properties.

Property | Description | Default
-------- | ----------- | -------
caption | Caption (horizontal) or label (vertical) for the input | -
type | Type of the input (could be set to almost all MODX input types[^1] and thumb for thumbnail display of image tvs[^2]) | text
elements | [Same options](http://rtfm.modx.com/evolution/1.0/developers-guide/template-variables/creating-a-template-variable) as in the *input option values* of a MODX template variable are possible i.e. for a dropdown with all documents in the MODX root: ``@SELECT `pagetitle`, `id` FROM `modx_site_content` WHERE parent = 0 ORDER BY `menuindex` ASC`` | -
default | Default value for the input. This value could contain calculated parts. There are two placeholders available: `{i}` contains an autoincremented index `{alias}` contains the alias of the edited document. | -
thumbof | Name of an image input. A thumbnail of the selected image will be rendered into this area | -
width | Width of the input | 100
{:.table .table-striped .table-hover}

[^1]: Supported MODX input types: text, rawtext, email, number, textareamini, textarea, rawtextarea, htmlarea, date, dropdown, listbox, listbox-multiple, checkbox, option, image, file
[^2]: See [images config](https://github.com/Jako/multiTV/blob/master/assets/tvs/multitv/configs/images.config.inc.php) for thumb

In datatable mode a layer will be displayed during adding/editing one row. In this editing layer the MODX input type richtext is possible.

### Columns

In *datatable* and *dbtable* mode the visible columns for the datatable could be defined in the key `columns`. This key contains an array of column settings. Each column setting contains an array of properties. If a property is not set, the field property in key `fields` is used.

Property | Description | Default
-------- | ----------- | -------
fieldname | **(required)** Fieldname that is displayed in this column | -
caption | Caption of the column | Caption for fieldname in `fields`
width | Width of the column | Width for fieldname in `fields`
render | Enable rengering of the column content with this PHx capable string | -
{:.table .table-striped .table-hover}

### Editing Layer

In *datatable* and *dbtable* mode the content of the editing layer could be defined in the key `form`. This key contains an array of form tab settings. Each form tab setting contains an array of field properties in the value of the content key. If a field property is not set, the field property in `fields` is used.

Property | Description | Default
-------- | ----------- | -------
caption | Caption for the input | Caption for fieldname in `fields`
{:.table .table-striped .table-hover}

### Default Output Templates

The default output templates for the multiTV snippet could be defined in the key `templates`.

Property | Description | Default
---- | ----------- | -------
rowTpl | Default row template chunk for the snippet output. Could be changed in snippet call. See [snippet documentation](/snippets.html) for possible placeholders | -
outerTpl | Default outer template chunk for the snippet output. Could be changed in snippet call. See [snippet documentation](/snippets.html) for possible placeholders | -
{:.table .table-striped .table-hover}

### Other options

The other options for one multiTV could be defined in the key `configuration`.

Property | Description | Default
---- | ----------- | -------
enablePaste | multiTV could contain *paste table data* link that displays a paste box. In this box you could paste Word/HTML table clipboard data, Google Docs table clipboard data and csv data. | true
enableClear | multiTV could contain *clear all* link that clears the content of the multiTV | true
csvseparator | Column separator for csv clipboard table data. The csv clipboard table data should contain a new line for each row. | ,
radioTabs | Tabs in the datatable editing layer are displayed as radio buttons. The button state is saved in *fieldTab* key of each multiTV row. | false
sorting | Enable sorting by column header in datatable mode. Row reordering by drag & drop will be disabled. | false
{:.table .table-striped .table-hover}

See the [multidemo config](https://github.com/Jako/multiTV/blob/master/assets/tvs/multitv/configs/multidemo.config.inc.php) for all usable vertical settings and the [multicontent config](https://github.com/Jako/multiTV/blob/master/assets/tvs/multitv/configs/multicontent.config.inc.php) for all usable datatable settings.