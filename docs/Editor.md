# The editor ✏️

The template editor is a core component of Templio, and we're dedicated to building the best and easiest editor - so you don't have to!

We have plans to support different type of editors, such as simple Rich Text/WYSIWYG and block-style editors, but for now we're focusing on building a great code editor.

[Templates](./Templates.md), [Layouts](./Layouts.md) and [Pre-processors](./Layouts) all share the same editor.

The editor has 3 sections or panes:

![Editor panes](../assets/images/editor_pane_overview.png)

## Left pane - Inputs

In this pane, you have all the inputs necessary for your template render, and it's easy to view/edit the inputs when editing your template.

### Preview Data

If your template needs `input data` to render, you can write in an example of the JSON data, and it will be used for the preview while you are working in the editor. The preview data will be saved, so you can quickly get started editing next time.

![Preview Data](../assets/images/preview_data.png)

If you have assigned any [pre-processors](https://templio.stoplight.io/docs/templio-docs/docs/Pre-processors.md) to your template, you will have the option to run the pre-processors on the input data you define, and the data will transform to the final state (after all pre-processors has run). You can easily switch back to the original preview data and trigger pre-proccesors to run again.

### Translations
If you are using translations, you can view all the keys and values in the translations pane.

![Translations pane](../assets/images/translations_editor_pane.png)

## Middle pane - Editor

This is where most of your time will be spent, building up your templates. The editor is using the popular [Ace](https://ace.c9.io/) code editor, customized for the best experience when building templates.

Together with the [Liquid](https://shopify.github.io/liquid/) templating language, you have all the power you need to build even the most advanced templates.


## Right pane - Preview

Being able to preview your templates as you write them is crucial, which is why we've built a live updating preview.

In the preview, you will see the final result, as we return it from the [Render API](https://templio.stoplight.io/docs/templio-docs/reference/Templio-API.v1.yaml/paths/~1render/post). You can switch between `HTML` and `PDF` preview.