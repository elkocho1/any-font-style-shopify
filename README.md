# Upload Custom Fonst Style to your Shopify Store
You can upload any font style to your Shopify store with this code 

This section lets you customize each heading, body or button element individually. You can upload as many custom fonts to your file manager and implement them in this section as u want. 

1. Copy this line of code to your theme.liquid file on the top of your body and click save

```
  {% section 'my-custom-fonts' %}

```

2. Create a new section and call it "my-custom-fonts.liquid"
3. Copy this line of code and paste it to this new section and click save.

```
{% if section.settings.enable %}
  <style data-custom-fonts>
    {% assign items = section.blocks | reverse  %}



      {% for block in items %}

      {% assign name = block.settings.name %}
      {% assign url = block.settings.custom_font_url  %}
      {% assign custom_font_weight = block.settings.custom_font_weight %}
      {% assign custom_font_style = block.settings.custom_font_style %}
      {% assign apply_h1 = block.settings.apply_h1 %}
      {% assign apply_h2 = block.settings.apply_h2 %}
      {% assign apply_h3 = block.settings.apply_h3 %}
      {% assign apply_h4 = block.settings.apply_h4 %}
      {% assign apply_h5 = block.settings.apply_h5 %}
      {% assign apply_h6 = block.settings.apply_h6 %}
      {% assign apply_span = block.settings.apply_span %}
      {% assign apply_p = block.settings.apply_p %}
      {% assign apply_custom = block.settings.apply_custom %}

      {% if url != blank and url != "" %}

        {% capture _font_type %}
        {% if url contains ".otf" %}
        opentype
        {% elsif url contains ".ttf" %}
        truetype
        {% elsif url contains ".svg" %}
        svg
        {% elsif url contains ".woff2" %}
        woff2
        {% else %}
        woff
        {% endif %}
        {% endcapture %}

        {% assign font_type = _font_type | strip %}
          @font-face {
            font-family: '{{ name }}';
            src: url({{ url }}) format('{{ font_type }}');

              {% if custom_font_style != 'none' %}
            font-style: {{ custom_font_style }};
              {% endif %}
            {% if custom_font_weight != 'none' %}
            font-weight: {{ custom_font_weight }};
              {% endif %}
          }


          {% if apply_h1 %}
            h1{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_h2 %}
            h2{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_h3 %}
            h3{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_h4 %}
            h4{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_h5 %}
            h5{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_h6 %}
            h6{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_p %}
            p{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_span %}
            span{
              font-family: '{{name}}' !important;
            }
          {% endif %}

          {% if apply_custom != "" and apply_custom != blank %}
            {{ apply_custom }}{
              font-family: '{{name}}' !important;
            }
          {% endif %}


      {% endif %}
      {% endfor %}
  </style>
{% endif %}

{% schema %}
{
  "name": "Custom Font",
  "settings": [
    {
      "type": "header",
      "content": "Custom Font Section"
    },
    {
      "type": "paragraph",
      "content": "Replace apps with copy/paste code snippets like this one & save money."
    },
    {
      "type": "checkbox",
      "id": "enable",
      "label": "Enable",
      "default": true
    }
  ],
  "blocks": [
    {
      "type": "image",
      "name": "Font",
      "settings": [
        {
          "type": "header",
          "content": "Custom Font Section"
        },
        {
          "type": "text",
          "id": "name",
          "label": "Custom font name",
          "info": "Use only lower or upper characters from A-Z. No numbers, no special characters, no spaces.",
          "default": "customfont"
        },
        {
          "type": "select",
          "id": "custom_font_weight",
          "label": "Font weight",
          "info": "If you're unsure, use \"none\".",
          "default": "none",
          "options": [
            {
              "value": "none",
              "label": "None"
            },
            {
              "value": "normal",
              "label": "Normal"
            },
            {
              "value": "bold",
              "label": "Bold"
            },
            {
              "value": "100",
              "label": "100"
            },
            {
              "value": "200",
              "label": "200"
            },
            {
              "value": "300",
              "label": "300"
            },
            {
              "value": "400",
              "label": "400"
            },
            {
              "value": "500",
              "label": "500"
            },
            {
              "value": "600",
              "label": "600"
            },
            {
              "value": "700",
              "label": "700"
            },
            {
              "value": "800",
              "label": "800"
            }
          ]
        },
        {
          "type": "select",
          "id": "custom_font_style",
          "label": "Font style",
          "info": "If you're unsure, use \"none\".",
          "default": "none",
          "options": [
            {
              "value": "none",
              "label": "None"
            },
            {
              "value": "normal",
              "label": "Normal"
            },
            {
              "value": "italic",
              "label": "Italic"
            }
          ]
        },
        {
          "type": "text",
          "id": "custom_font_url",
          "label": "Custom font URL",
          "info": "Add all URLs for this font here, one per line. Upload your fonts to the [files panel](/admin/settings/files)."
        },
        {
          "type": "paragraph",
          "content": "Apply the custom font to the following HTML elements:"
        },
        {
          "type": "checkbox",
          "id": "apply_h1",
          "label": "H1",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_h2",
          "label": "H2",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_h3",
          "label": "H3",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_h4",
          "label": "H4",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_h5",
          "label": "H5",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_h6",
          "label": "H6",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_span",
          "label": "<span> tags",
          "info": "Apply this custom font to all HTML span elements.",
          "default": true
        },
        {
          "type": "checkbox",
          "id": "apply_p",
          "label": "<p> tags",
          "info": "Apply this custom font to all HTML paragraph elements.",
          "default": true
        },
        {
          "type": "textarea",
          "id": "apply_custom",
          "label": "CSS Selectors",
          "info": "Apply font to custom CSS selectors. Example: .custom-text,.wrapper > h1",
          "placeholder": ".my-text"
        }
      ]
    }
  ]
}
{% endschema %}



```

4. Go to you theme customizer and look for you new section on. 

