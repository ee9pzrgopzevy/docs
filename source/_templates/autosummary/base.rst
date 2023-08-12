..
    We use short name as title, because it's part of TOC tree on the left hand nav.
    Then we fix the HTML title in the templating.

{{ name | escape | underline}}

.. currentmodule:: {{ module }}

.. meta::
    :description: {{ fullname|extract_object_docstring }}
    :title: {{ name }} {{ objtype }} in {{ fullname|extract_mod_path }}

{% if objtype == "class" %}

Documentation for `{{ fullname }}` Python class.

.. autoclass:: {{ objname }}
   :members:

   {% block attributes %}
   {% if attributes %}
   .. rubric:: {{ _('Attributes summary') }}

   .. autosummary::
   {% for item in attributes %}
      ~{{ name }}.{{ item }}
   {%- endfor %}
   {% endif %}
   {% endblock %}

   {% block methods %}
   {% if methods %}
   .. rubric:: {{ _('Methods summary') }}

   .. autosummary::
   {% for item in methods %}
      ~{{ name }}.{{ item }}
   {%- endfor %}
   {% endif %}
   {% endblock %}

{% else %}

Documentation for `{{ fullname }}` Python {{ objtype }}.

.. auto{{ objtype }}:: {{ objname }}
{% endif %}


