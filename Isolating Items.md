# Isolating specific elements within a shader

## GUI
Some shaders also affect items in inventories or other components in GUIs. To prevent customized shaders from altering these parts, you could exclude customized code based on depth that can be obtained as `float depth = -(ModelViewMat * vec4(1.0)).z;`.

**Exception**: `entity_cutout_no_cull_z_offset` have z offset by `0.0039`, so subtract this value from dist in this shader.

Also you can isolate gui components by `ProjMat[3].x == -1`.

### Table of depths for GUI components (items)
<table>
<thead>
  <tr>
    <th>Component</th>
    <th>depth value</th>
    <th>Affected by shaders</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Advancement pop-out icons</td>
    <td>1034</td>
    <td rowspan="7">entity_cutout<br>entity_no_outline<br>entity_solid<br>entity_cutout_no_cull<br>entity_translucent_cull<br>entity_cutout_no_cull_z_offset<br>glint_direct <br>glint_translucent</td>
  </tr>
  <tr>
    <td>Selected advancement icons</td>
    <td rowspan="2">1434</td>
  </tr>
  <tr>
    <td>Items in bundle</td>
  </tr>
  <tr>
    <td>Items that are being moved between slots</td>
    <td>1602</td>
  </tr>
  <tr>
    <td>Items in inventory</td>
    <td>1734</td>
  </tr>
  <tr>
    <td>Advancement icons</td>
    <td rowspan="2">1834</td>
  </tr>
  <tr>
    <td>Items in hotbar</td>
  </tr>
  <tr>
    <td>Player doll in inventory</td>
    <td>951</td>
    <td>entity_translucent</td>
  </tr>
  <tr>
    <td>Armor on player doll in inventory</td>
    <td>950.99978</td>
    <td>rendertype_armor_cutout_no_cull<br>armor_entity_glint</td>
  </tr>
</tbody>
</table>

### Position in gui:
As you can see, some elements have equal depth so it need to be isolated other way.

For example, we can isolate hotbar with additional check if item is on line of hotbar like this:
```glsl
vec2 ScrSize = ceil(2 / vec2(ProjMat[0][0], -ProjMat[1][1]));
vec2 Pos = ModelViewMat[3].xy;
...
if (dist == 1834 && ScrSize.y - pos.y <= 13)
{
  //code...
}
```
`ScrSize` and `Pos` from this code may be used for modification of items in GUI.