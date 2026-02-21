---
layout: default
title: MATLAB Version History
---

# MATLAB Version History

MathWorks has released a new version of MATLAB twice annually since 2006. The table below displays the MATLAB version number, release name, release number <a href="#note-release_number">*)</a>, release date, bundled JVM version (for Windows), new product introductions (since R2012b) and product changes (since R2011a).

See the [repository](https://github.com/jorikcaljouw/MATLAB-Release-Info) for planned enhancements and for giving feedback on this page.

<a id="note-release_number"></a>*) The release number is the version number reported by Concurrent License Manager program [FLEXlm](https://en.wikipedia.org/wiki/FlexNet_Publisher) and this number can also be seen in the license file.

<table>
<thead>
  <tr>
    <th>Version</th>
    <th>Name</th>
    <th>Number</th>
    <th>Date</th>
    <th>Bundled JVM</th>
    <th>New Product</th>
    <th>Product Changes</th>
  </tr>
</thead>
<tbody>
  {% for item in site.data.matlab_history reversed %}
  <tr>
    <td>{{ item.version }}</td>
    <td>{{ item.release_name }}</td>
    <td>{{ item.license_number }}</td>
    <td>{{ item.release_date }}</td>
    <td>{{ item.jvm }}</td>
    <td>
      {%- assign prod_count = item.new_product | size -%}

      {%- if prod_count > 1 -%}
        <ul>
          {%- for prod in item.new_product -%}
            <li>{{ prod }}</li>
          {%- endfor -%}
        </ul>
      {%- elsif prod_count == 1 -%}
        {{ item.new_product[0] }}
      {%- endif -%}
    </td>
    <td>
      {%- assign prod_count = item.product_changes | size -%}

      {%- if prod_count > 1 -%}
        <ul>
          {%- for prod in item.product_changes -%}
            <li>{{ prod }}</li>
          {%- endfor -%}
        </ul>
      {%- elsif prod_count == 1 -%}
        {{ item.product_changes[0] }}
      {%- endif -%}
    </td>
  </tr>
  {% endfor %}
</tbody>
</table>
