# shopify-sections

A personal library of reusable, theme-agnostic Shopify sections and snippets. Designed for OS 2.0 themes, configurable from the Customizer, with no hardcoded content.

## Conventions

- Sections live in [sections/](./sections/) and are named `custom-[name].liquid`
- Reusable parts live in [snippets/](./snippets/)
- Original theme files are never edited — every section is a standalone, drop-in addition
- Every visual element is exposed as a schema setting or block setting
- Mobile-first CSS, no `!important`, no inline styles

## Section template

```liquid
{% comment %} Section: custom-[name] — [purpose] {% endcomment %}

<div class="custom-[name] section-{{ section.id }}">
  {%- if section.settings.heading != blank -%}
    <h2>{{ section.settings.heading }}</h2>
  {%- endif -%}
</div>

{% style %}
  .section-{{ section.id }} {
    padding-top: {{ section.settings.padding_top }}px;
    padding-bottom: {{ section.settings.padding_bottom }}px;
  }
{% endstyle %}

{% schema %}
{
  "name": "Section Name",
  "settings": [
    { "type": "text", "id": "heading", "label": "Heading" },
    { "type": "range", "id": "padding_top", "label": "Padding top", "min": 0, "max": 100, "step": 4, "default": 40 },
    { "type": "range", "id": "padding_bottom", "label": "Padding bottom", "min": 0, "max": 100, "step": 4, "default": 40 }
  ],
  "presets": [{ "name": "Section Name" }]
}
{% endschema %}
```

## Usage

Drop a `.liquid` file from `sections/` or `snippets/` into the matching folder of any OS 2.0 theme. The section will appear in the Theme Customizer under "Add section".

## License

MIT
