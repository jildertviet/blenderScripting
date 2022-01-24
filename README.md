# Blender + Python example

To execute the script, press: Alt + P while cursor is in Text Editor.

Python file is:
```
import bpy
import random

bpy.ops.object.select_all(action='DESELECT')
bpy.ops.object.select_by_type(type='MESH')
bpy.ops.object.delete()

print("All meshes deleted")

#sizes = [1, 0.5, 0.5, 0.25, 0.125]
sizes = [1]
spaceRange = 4

def r(): # Shorter random function, ranged -1 <> 1
    return (random.random() - 0.5) * 2

for i in range(0,100):
    bpy.ops.mesh.primitive_cube_add()
    cube = bpy.context.selected_objects[0]
    size = random.choice(sizes)
    cube.dimensions = (size, size, size / 4)
    cube.data.materials.append(bpy.data.materials['CubeMaterial'])
    cube.location = (r() * spaceRange, r() * spaceRange, r() * spaceRange)
```
