---
layout: default
title: MATLAB Version History
---

# MATLAB Version History

MathWorks releases a new version of MATLAB twice annually since 2016. The table below displays the version number, release "name", license number as shown in license files and release date per version. Additional columns will be added shortly including information about newly introduced products, and any changes or transitions in product names.

<table>
<thead>
  <tr>
    <th>Version</th>
    <th>Release Name</th>
    <th>License Number</th>
    <th>Release Date</th>
  </tr>
</thead>
<tbody>
  {% for item in site.data.matlab_history %}
  <tr>
    <td>{{ item.version }}</td>
    <td>{{ item.release_name }}</td>
    <td>{{ item.license_number }}</td>
    <td>{{ item.release_date }}</td>
  </tr>
  {% endfor %}
</tbody>
</table>
