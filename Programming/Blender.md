## Sample codes
### Move mesh vertices
```py
for v in bpy.data.objects['Cube.001'].data.vertices:
    v.co.x += 1.0
```

### Print Object List
```py
for obj in bpy.data.objects:
   print(obj)
print('')
```

### Print Object Property list
```py
for obj in bpy.data.objects:
    for att in dir(obj):
        print(att)
```

### Create & Remove Mesh
```py
mesh = bpy.data.meshes.new(name="MyMesh")
bpy.data.meshes.remove(mesh)
```

### Create empty Object
```py
bpy.ops.object.add()
bpy.context.active_object.name = 'TestEmpty'
```

### Create Mesh Object
+ Empty mesh
```py
bpy.ops.object.add(type='MESH')
bpy.context.active_object.name = 'TestMesh'
```

+ Plane
```py
# https://blender.stackexchange.com/questions/61879/create-mesh-then-add-vertices-to-it-in-python
mesh = bpy.data.meshes.new("TestMesh") 
obj = bpy.data.objects.new(mesh.name, mesh)
col = bpy.data.collections["Collection"]
col.objects.link(obj)
bpy.context.view_layer.objects.active = obj

verts = [( 1.0,  1.0,  0.0), 
         ( 1.0, -1.0,  0.0),
         (-1.0, -1.0,  0.0),
         (-1.0,  1.0,  0.0),
         ]  # 4 verts made with XYZ coords
edges = []
faces = [[0, 1, 2, 3]]

mesh.from_pydata(verts, edges, faces)
```

+ Lattice
```py
import bpy
mesh = bpy.data.meshes.new("TestMesh") 
obj = bpy.data.objects.new(mesh.name, mesh)
col = bpy.data.collections["Collection"]
col.objects.link(obj)
bpy.context.view_layer.objects.active = obj

verts = []
edges = []
faces = []

vertcnt = 0
vertDist = 0.5
for i in range(10):
    for j in range(10):
        verts.append(  (vertDist * (i + 1), vertDist * (j + 1), 0.0)  )
        verts.append(  (vertDist * (i + 1), vertDist * j, 0.0)  )
        verts.append(  (vertDist * i, vertDist * j, 0.0)  )
        verts.append(  (vertDist * i, vertDist * (j + 1), 0.0)  )
        vertcnt += 4
        faces.append([vertcnt - 4, vertcnt - 3, vertcnt - 2, vertcnt - 1])
        
mesh.from_pydata(verts, edges, faces)
```

### Print Object operation list
```py
for prop in dir(bpy.ops.object):
    print(prop)
```

## Operation Domains
```
action
anim
armature
asset
boid
brush
buttons
cachefile
camera
clip
cloth
collection
console
constraint
curve
curves
cycles
dpaint
ed
export_anim
export_mesh
export_scene
file
fluid
font
geometry
gizmogroup
gpencil
graph
image
import_anim
import_curve
import_mesh
import_scene
info
lattice
marker
mask
material
mball
mesh
nla
node
object
outliner
paint
paintcurve
palette
particle
pose
poselib
preferences
ptcache
render
rigidbody
scene
screen
script
sculpt
sculpt_curves
sequencer
sound
spreadsheet
surface
text
texture
transform
ui
uilist
uv
view2d
view3d
wm
workspace
world
```
### Mesh Operation List
```
attribute_set
average_normals
beautify_fill
bevel
bisect
blend_from_shape
bridge_edge_loops
colors_reverse
colors_rotate
convex_hull
customdata_bevel_weight_edge_add
customdata_bevel_weight_edge_clear
customdata_bevel_weight_vertex_add
customdata_bevel_weight_vertex_clear
customdata_crease_edge_add
customdata_crease_edge_clear
customdata_crease_vertex_add
customdata_crease_vertex_clear
customdata_custom_splitnormals_add
customdata_custom_splitnormals_clear
customdata_mask_clear
customdata_skin_add
customdata_skin_clear
decimate
delete
delete_edgeloop
delete_loose
dissolve_degenerate
dissolve_edges
dissolve_faces
dissolve_limited
dissolve_mode
dissolve_verts
dupli_extrude_cursor
duplicate
duplicate_move
edge_collapse
edge_face_add
edge_rotate
edge_split
edgering_select
edges_select_sharp
extrude_context
extrude_context_move
extrude_edges_indiv
extrude_edges_move
extrude_faces_indiv
extrude_faces_move
extrude_manifold
extrude_region
extrude_region_move
extrude_region_shrink_fatten
extrude_repeat
extrude_vertices_move
extrude_verts_indiv
face_make_planar
face_set_extract
face_split_by_edges
faces_mirror_uv
faces_select_linked_flat
faces_shade_flat
faces_shade_smooth
fill
fill_grid
fill_holes
flip_normals
flip_quad_tessellation
hide
inset
intersect
intersect_boolean
knife_project
knife_tool
loop_multi_select
loop_select
loop_to_region
loopcut
loopcut_slide
mark_freestyle_edge
mark_freestyle_face
mark_seam
mark_sharp
merge
merge_normals
mod_weighted_strength
normals_make_consistent
normals_tools
offset_edge_loops
offset_edge_loops_slide
paint_mask_extract
paint_mask_slice
point_normals
poke
polybuild_delete_at_cursor
polybuild_dissolve_at_cursor
polybuild_extrude_at_cursor_move
polybuild_face_at_cursor
polybuild_face_at_cursor_move
polybuild_split_at_cursor
polybuild_split_at_cursor_move
polybuild_transform_at_cursor
polybuild_transform_at_cursor_move
primitive_circle_add
primitive_cone_add
primitive_cube_add
primitive_cube_add_gizmo
primitive_cylinder_add
primitive_grid_add
primitive_ico_sphere_add
primitive_monkey_add
primitive_plane_add
primitive_torus_add
primitive_uv_sphere_add
quads_convert_to_tris
region_to_loop
remove_doubles
reveal
rip
rip_edge
rip_edge_move
rip_move
screw
select_all
select_axis
select_face_by_sides
select_interior_faces
select_less
select_linked
select_linked_pick
select_loose
select_mirror
select_mode
select_more
select_next_item
select_non_manifold
select_nth
select_prev_item
select_random
select_similar
select_similar_region
select_ungrouped
separate
set_normals_from_faces
shape_propagate_to_all
shortest_path_pick
shortest_path_select
smooth_normals
solidify
sort_elements
spin
split
split_normals
subdivide
subdivide_edgering
symmetrize
symmetry_snap
tris_convert_to_quads
unsubdivide
uv_texture_add
uv_texture_remove
uvs_reverse
uvs_rotate
vert_connect
vert_connect_concave
vert_connect_nonplanar
vert_connect_path
vertices_smooth
vertices_smooth_laplacian
wireframe
```

### Object operation list
```
add
add_named
align
anim_transforms_to_deltas
armature_add
assign_property_defaults
bake
bake_image
camera_add
clear_override_library
collection_add
collection_external_asset_drop
collection_instance_add
collection_link
collection_objects_select
collection_remove
collection_unlink
constraint_add
constraint_add_with_targets
constraints_clear
constraints_copy
convert
correctivesmooth_bind
curves_empty_hair_add
curves_random_add
data_instance_add
data_transfer
datalayout_transfer
delete
drop_geometry_nodes
drop_named_image
drop_named_material
duplicate
duplicate_move
duplicate_move_linked
duplicates_make_real
editmode_toggle
effector_add
empty_add
explode_refresh
face_map_add
face_map_assign
face_map_deselect
face_map_move
face_map_remove
face_map_remove_from
face_map_select
forcefield_toggle
geometry_node_tree_copy_assign
geometry_nodes_input_attribute_toggle
geometry_nodes_move_to_nodes
gpencil_add
gpencil_modifier_add
gpencil_modifier_apply
gpencil_modifier_copy
gpencil_modifier_copy_to_selected
gpencil_modifier_move_down
gpencil_modifier_move_to_index
gpencil_modifier_move_up
gpencil_modifier_remove
hide_collection
hide_render_clear_all
hide_view_clear
hide_view_set
hook_add_newob
hook_add_selob
hook_assign
hook_recenter
hook_remove
hook_reset
hook_select
instance_offset_from_cursor
instance_offset_from_object
instance_offset_to_cursor
isolate_type_render
join
join_shapes
join_uvs
laplaciandeform_bind
light_add
lightprobe_add
lightprobe_cache_bake
lightprobe_cache_free
lineart_bake_strokes
lineart_bake_strokes_all
lineart_clear
lineart_clear_all
link_to_collection
load_background_image
load_reference_image
location_clear
make_dupli_face
make_links_data
make_links_scene
make_local
make_override_library
make_single_user
material_slot_add
material_slot_assign
material_slot_copy
material_slot_deselect
material_slot_move
material_slot_remove
material_slot_remove_unused
material_slot_select
meshdeform_bind
metaball_add
mode_set
mode_set_with_submode
modifier_add
modifier_apply
modifier_apply_as_shapekey
modifier_convert
modifier_copy
modifier_copy_to_selected
modifier_move_down
modifier_move_to_index
modifier_move_up
modifier_remove
modifier_set_active
move_to_collection
multires_base_apply
multires_external_pack
multires_external_save
multires_higher_levels_delete
multires_rebuild_subdiv
multires_reshape
multires_subdivide
multires_unsubdivide
ocean_bake
origin_clear
origin_set
parent_clear
parent_inverse_apply
parent_no_inverse_set
parent_set
particle_system_add
particle_system_remove
paths_calculate
paths_clear
paths_update
paths_update_visible
pointcloud_add
posemode_toggle
quadriflow_remesh
quick_explode
quick_fur
quick_liquid
quick_smoke
randomize_transform
reset_override_library
rotation_clear
scale_clear
select_all
select_by_type
select_camera
select_grouped
select_hierarchy
select_less
select_linked
select_mirror
select_more
select_pattern
select_random
select_same_collection
shade_flat
shade_smooth
shaderfx_add
shaderfx_copy
shaderfx_move_down
shaderfx_move_to_index
shaderfx_move_up
shaderfx_remove
shape_key_add
shape_key_clear
shape_key_mirror
shape_key_move
shape_key_remove
shape_key_retime
shape_key_transfer
simulation_nodes_cache_bake
simulation_nodes_cache_calculate_to_frame
simulation_nodes_cache_delete
skin_armature_create
skin_loose_mark_clear
skin_radii_equalize
skin_root_mark
speaker_add
subdivision_set
surfacedeform_bind
text_add
track_clear
track_set
transfer_mode
transform_apply
transform_axis_target
transform_to_mouse
transforms_to_deltas
unlink_data
vertex_group_add
vertex_group_assign
vertex_group_assign_new
vertex_group_clean
vertex_group_copy
vertex_group_copy_to_selected
vertex_group_deselect
vertex_group_invert
vertex_group_levels
vertex_group_limit_total
vertex_group_lock
vertex_group_mirror
vertex_group_move
vertex_group_normalize
vertex_group_normalize_all
vertex_group_quantize
vertex_group_remove
vertex_group_remove_from
vertex_group_select
vertex_group_set_active
vertex_group_smooth
vertex_group_sort
vertex_parent_set
vertex_weight_copy
vertex_weight_delete
vertex_weight_normalize_active_vertex
vertex_weight_paste
vertex_weight_set_active
visual_transform_apply
volume_add
volume_import
voxel_remesh
voxel_size_edit
```