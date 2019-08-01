Simple example of getting a CAD model (e.g. STP) into Gazebo.
First convert the CAD file format to a mesh file format (e.g. STL or Collada), for example by using FreeCAD (see also (here)[http://andreasbihlmaier.github.io/2014/02/11/open-source_workflow_for_gazebo_models.html]).
Also create a simple convex mesh as collision object (e.g. using Blender modifiers or MeshLab's "Convex Hull" filter) or use a (several) geometric primitive(s) as `<collision>`.

Layout suggestion for model "cool gadget":
* cool_gadget/
  * materials/    Gazebo: OGRE materials
  * meshes/       Mesh formats (.dae, .stl, .iv)
  * modeling/     CAD software files
  * solids/       CAD formats (.step, .dxf)
  * model.config  Gazebo: Metainformation about cool_gadget
  * model.sdf     Gazebo: SDF (describes links (collision, visual) connected by joints togehter with plugins)

The only files mandatory to make the model work in Gazebo ([and publish it to rviz](http://andreasbihlmaier.github.io/2014/02/19/gazebo2rviz.html)) or to [convert it to URDF](http://wiki.ros.org/pysdf) are:
* model.sdf
* model.config
* meshes/

Add the following line to your `~./bashrc`, but replace `full_path_to_this_repository` with the actual absolute path to the directory containing this README.md. 
```
export GAZEBO_MODEL_PATH="$GAZEBO_MODEL_PATH:full_path_to_this_repository"
```
Then start `gazebo` (e.g. `roslaunch gazebo_ros empty_world.launch`) in a _new_ terminal and the model should be available from the Insert tab.
