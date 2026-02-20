---
layout: default
title: MATLAB Version History
---

# MATLAB Version History

MathWorks has released a new version of MATLAB twice annually since 2016. The table below displays the MATLAB version number, release "name", (release) number, release date and bundled JVM version (for Windows). See the [repository](https://github.com/jorikcaljouw/MATLAB-Release-Info) for planned enhancements and for giving feedback on this page.
The release number is the version reported by Concurrent License Manager program [FLEXlm](https://en.wikipedia.org/wiki/FlexNet_Publisher) and this number can also be seen in the license file.

<table>
<thead>
  <tr>
    <th>Version</th>
    <th>Release Name</th>
    <th>Number</th>
    <th>Release Date</th>
    <th>Bundled JVM</th>
    <th>New Product</th>
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
    <td>{{ item.new_product | join: '; ' }}</td>
  </tr>
  {% endfor %}
</tbody>
</table>
