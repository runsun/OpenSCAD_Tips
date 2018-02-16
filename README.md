# OpenSCAD Tips

| $ **Official help** |
|----------------------|
|[OpenSCAD language ref](https://en.wikibooks.org/wiki/OpenSCAD_User_Manual/The_OpenSCAD_Language) |
|Cheet sheet: [Official](http://www.openscad.org/cheatsheet/), [KitWallace's](http://kitwallace.co.uk/openscad/OpenSCAD%20CheatSheet.htm) |
|[Work in Progress](https://en.wikibooks.org/wiki/OpenSCAD_User_Manual/WIP) |
|[Nightly snapshots](http://files.openscad.org/snapshots/) |
|[OpenSCAD forum](http://forum.openscad.org)|
|[OpenSCAD freenode IRC](http://webchat.freenode.net/?channels=#openscad)|

| $ **tips** | 
|------------|
| [animation](http://forum.openscad.org/About-animation-just-for-the-record-just-for-Windows-users-td16733.html) ( [gif](http://forum.openscad.org/Animating-gif-with-3D-rotation-tp14011.html), [prodVid](http://forum.openscad.org/Product-Video-produced-with-OpenSCAD-td15783.html), [animlib](http://forum.openscad.org/Animation-Motion-Library-td17196.html), [imgsize](http://forum.openscad.org/Can-I-force-Animation-to-use-quot-Render-quot-instead-of-quot-Preview-quot-td14828.html#a14848), [JordanBrown](http://forum.openscad.org/matrix-interpolation-td22284.html)) |
| [area](http://forum.openscad.org/Easy-way-to-get-the-area-of-a-polygon-tp17045p17055.html) |
| Associated Array: See hash below |
| [Bezier](http://forum.openscad.org/Can-you-sweep-a-object-with-fingers-tp19057p19309.html), Eric Buijs' [PolyBeziers](https://plus.google.com/104802930025458639218/posts/VZrXMxLd8Mt) |
| Bounding box (1) [doc](https://en.wikibooks.org/wiki/OpenSCAD_User_Manual/Commented_Example_Projects) handles only one obj; (2) [Ronaldo](http://forum.openscad.org/Round-anything-Retrospective-rounding-filleting-module-tp21794p21820.html) handles one or more; (3) [Ronaldo's 2d](http://forum.openscad.org/Getting-2D-bounding-box-dimensions-td23256.html) | 
| [Chinese font](http://forum.openscad.org/How-to-write-a-texture-to-a-face-Solid-in-a-geometric-model-tp16718p16753.html) |
| color/HTML color: [MichaelAtOz](https://github.com/openscad/openscad/files/1250754/rgb.txt) |
| Commandline [Enable Exp Features](http://forum.openscad.org/Enable-experimental-features-concat-text-in-command-line-td9287.html#a9290), [Set parameters and rotation](http://forum.openscad.org/Animating-gif-with-3D-rotation-td14011.html#a14029) |
| [Curved Image](http://forum.openscad.org/Images-on-curved-cylindrical-surface-td17823.html) |
| Curve Text: [JustinSDK](http://openhome.cc/eGossip/OpenSCAD/ModifierCharacters.html), [MichaelAtOz](http://forum.openscad.org/textCylinder-dodgy-version-for-text-around-a-cylinder-td9262.html#a9265) |
| Degenerate polygon [Ronaldo](http://forum.openscad.org/Polyhedron-degenerated-triangles-are-allowed-but-quads-td19917.html) |
| Data Structure [NateTG's 2-3 tree](http://forum.openscad.org/Programming-in-Functional-OpenSCAD-td23039.html), [Good 2-3 ref](http://cs.wellesley.edu/~cs230/fall02/2-3-trees.pdf), [thehans' L-system](http://forum.openscad.org/L-systems-demo-Fractal-designs-interpreter-performance-stress-testing-td23295.html)([github](https://gist.github.com/thehans/a1494db8046a58832e2ebb10a5908a66))|
| Dimensioning: Don Smiley's dimlines: [new ver](http://forum.openscad.org/Dimension-Parameter-labeling-for-part-diagrams-tp15172p15185.html), [doc](http://www.cannymachines.com/entries/9/openscad_dimensioned_drawings) |
| Editor ([Quick ref on browser by Len Trigg](http://forum.openscad.org/Poor-mans-quick-help-lookup-for-openscad-built-in-modules-td23242.html)) |
| [excel-control](http://forum.openscad.org/Parameterlist-Excel-export-to-OpenSCAD-tp15363p15367.html) |
| Flatten surface: [nophead's](http://forum.openscad.org/flattening-curved-surfaces-tp19727p19763.html), [runsun's](http://forum.openscad.org/flattening-curved-surfaces-tp19727p19782.html), [osresearch papercraft](https://github.com/osresearch/papercraft), [Parkinbot's](http://forum.openscad.org/flattening-curved-surfaces-tp19727p19807.html) |
| [$fa,$fs,$fn](http://forum.openscad.org/better-than-fn-get-fs-working-a-tutorial-td1271.html), [1](http://forum.openscad.org/fn-fa-and-fs-tp17932p17936.html),[Ian](https://forum.makehackvoid.com/t/openscad-circle-calculations/721) |
| [gear](http://lcamtuf.coredump.cx/gcnc/ch6/#6.1), [Parkinbot](http://www.thingiverse.com/thing:636119) |
| Geodisc [William Adams](https://www.thingiverse.com/thing:10725),[2](https://www.thingiverse.com/thing:10540), [Yona Appletree](https://gist.github.com/Yona-Appletree/a03bc32a5c5ca6886e38)|
| hash: [1](http://forum.openscad.org/parameterized-models-td8303.html#a8306), [2](http://forum.openscad.org/Can-I-get-some-code-review-up-in-here-tp12341p12355.html), [Search-based hash](http://www.thingiverse.com/groups/openscad/topic:5610#comment-1093645) |
| [isosphere](http://forum.openscad.org/New-Algorithm-for-Spheres-tp13306p17062.html)([2](http://blog.andreaskahler.com/2009/06/creating-icosphere-mesh-in-code.html)) |
| [lerp](http://forum.openscad.org/Irregular-mesh-generated-tp13765p13779.html ) |
| [Lazy Union by Parkinbot](http://forum.openscad.org/rendering-for-paper-assembly-manual-tp20108p20126.html), [Ronaldo's](http://forum.openscad.org/rendering-for-paper-assembly-manual-tp20108p20140.html) |
| [makefile](http://forum.openscad.org/Makefile-for-building-complex-models-from-a-single-file-td22296.html ) |
| [matrix](http://www.thingiverse.com/thing:10249/#files)([2](http://forum.openscad.org/restrict-hull-function-to-one-or-two-dimensions-tp16696p16722.html),[3](https://github.com/lhartmann/openscad_m4lib/blob/master/m4.scad)); [invert](https://github.com/openscad/openscad/issues/1040#issuecomment-233208606) |  
| Packaging: [1](http://forum.openscad.org/Managing-libraries-and-modules-in-complex-projects-td23200.html) |
| Parser: [runsun's scadx_match](https://bitbucket.org/runsun/scadx/src/f144a5d77e534ae81d712e41bd5e89d8a8629ab4/scadx_match.scad?at=master&fileviewer=file-view-default), [Parkinbot's stl parser](http://forum.openscad.org/flattening-curved-surfaces-tp19727p19816.html), [APruss' Function parser](https://www.thingiverse.com/thing:2295309), [Carl Davidson's string.scad](https://github.com/davidson16807/relativity.scad/blob/master/strings.scad) |
| [precision](http://forum.openscad.org/Inconsistent-conversion-of-floating-number-to-string-at-7th-significant-digit-tp14350.html)([2](http://forum.openscad.org/Simple-addition-of-numbers-introduces-error-td14408.html)) |
| [RGB](http://forum.openscad.org/An-HSV-HSB-to-RGB-Color-function-in-OpenSCAD-td9835.html) |
| Round Anything by [irev dev](https://www.thingiverse.com/thing:2419664) |
| Rounded Cube [Parkinbot](http://forum.openscad.org/Functional-OpenSCAD-working-with-vertex-data-tp21080p23072.html), [Parkinbot new](http://forum.openscad.org/Functional-OpenSCAD-working-with-vertex-data-tp21080p23064.html) |
| [rounded polygon](http://forum.openscad.org/Script-to-replicate-hull-and-minkoswki-for-CSG-export-import-into-FreeCAD-td16537.html) |
| Search(): [details](http://forum.openscad.org/Digging-into-search-td12421.html) |
| Shelling: [jweoblog](http://jweoblog.com/?p=644) |
| Sphere [1](http://forum.openscad.org/New-Algorithm-for-Spheres-td13306.html#a17087) |
| Spline [1](http://forum.openscad.org/Modelling-a-flexible-strip-td22645.html) |
| Spring: [Parkinbot](http://forum.openscad.org/how-to-make-the-groove-more-width-tp20154p20158.html) |
| [sweep](https://github.com/openscad/list-comprehension-demos/blob/master/sweep.scad) ([1](http://forum.openscad.org/Two-annoyances-td12935i20.html#a13110),[2](http://forum.openscad.org/Vertex-arrays-tp15876p15969.html),[3](http://forum.openscad.org/file/n18324/sweep2.scad)), [Benjemin Easing Func](http://forum.openscad.org/Sweep-with-easing-equations-td20075.html)|
| [tail Recursion](http://forum.openscad.org/Simple-polygon-triangulation-tp16755p16941.html)([2](http://forum.openscad.org/Simple-polygon-triangulation-tp16755p16962.html),[3](http://forum.openscad.org/Tail-recursion-td17040.html),[4](http://forum.openscad.org/Simple-polygon-triangulation-tp16755p16941.html)) |
| [text](http://forum.openscad.org/Wrapping-text-around-a-complex-geometry-tc18145.html), [Carl Davidson's str lib](https://www.thingiverse.com/thing:526023), [Chambered](http://forum.openscad.org/Chamfered-3D-text-td23162.html) | 
| testing: [tests in OpenSCAD](http://forum.openscad.org/Clarifying-behaviors-tp18492p18507.html)([2](http://forum.openscad.org/tests-in-OpenSCAD-td8978.html),[3](https://github.com/openscad/openscad/blob/master/doc/testing.txt)), [RoyaSutton](http://forum.openscad.org/Doxygen-openscad-amu-and-omdl-Documenting-and-Design-Flow-td19924.html)([pdf](https://cdn.thingiverse.com/assets/3c/16/d2/00/ea/refman.pdf)), [runsun's doctest](https://github.com/runsun/openscad_doctest)|
| [triangulation](http://forum.openscad.org/Simple-polygon-triangulation-td16755.html) |
| Tube: [Ronaldo's](http://forum.openscad.org/file/n19680/Tube_example.scad), [Runsun's](http://forum.openscad.org/Bent-rod-td14003.html), [Johan's](http://forum.openscad.org/method-to-sweep-or-skin-a-hollow-object-without-difference-function-tp19677p19688.html) |
| [type-checking](http://forum.openscad.org/Determining-what-data-type-a-variable-is-holding-tp16111p16126.html) |
| [unit](http://forum.openscad.org/Output-inch-hardware-sizes-td19204.html) |
| [variable](http://forum.openscad.org/Ignoring-unknown-variable-issue-tp13156p13321.html)([2](http://forum.openscad.org/Special-Variables-tp14477p14512.html)) |
| [volume/center](http://forum.openscad.org/Volume-and-Center-of-mass-td15421.html) |
| [Warning, User](http://forum.openscad.org/Sweep-with-easing-equations-td20075.html) |
| Wavy solid: [Parkinbot's](http://forum.openscad.org/Sweeping-a-cone-through-a-range-of-angles-about-the-origin-tp19662p19676.html) |

|$ **My libs** |
|---------------------|
| [scadx](https://bitbucket.org/runsun/scadx) |
| [doctest](https://github.com/runsun/openscad_doctest) |
| [faces](http://forum.openscad.org/A-faces-function-for-simple-polyhedrons-td12809.html)([git](https://github.com/runsun/faces.scad)) |
| [offline doc](http://forum.openscad.org/Use-openscad-offliner-for-offline-documentation-td13096.html)([git](https://github.com/runsun/openscad_offliner)) |
| [runscad.py](http://forum.openscad.org/Animating-gif-with-3D-rotation-tp14011p14029.html)([2](http://forum.openscad.org/Symmetrical-Rotation-tp14062p14075.html), [git](https://gist.github.com/runsun/995250a8002386ab9abc)) |
| [synwrite](http://forum.openscad.org/Happy-New-Year-OpenSCAD-syntax-lexer-for-SynWrite-td15402.html)([2](http://www.thingiverse.com/thing:1237864)), [CudaText](http://forum.openscad.org/Syntax-highlighting-tp23247p23258.html) |

| $ **tools** |
| ----------------------------------------|
|[Daid's Polygon maker](http://daid.eu/~daid/3d/) |
|[Polygon Rabbit](http://www.protorabbit.nl/flash/polygonrabbit/PolygonRabbit.html)|
|[STL viewers](http://forum.openscad.org/looking-for-a-good-STL-viewer-locally-application-td19722.html)| 
|[Smithsonia X3D explorer](http://3d.si.edu/explorer?modelid=1341)|
|[SVGNesting](http://svgnest.com/)|
|[SketchPad](http://studio.sketchpad.cc/sp/account/sign-in?cont=http%3a%2f%2fstudio.sketchpad.cc%2f)|
|[GoJS polygon drawing](http://gojs.net/latest/extensions/PolygonDrawing.html?gclid=CNmkgNW0ldECFY22wAodAH8EZQ)|
|[osresearch papercraft](https://github.com/osresearch/papercraft) |
|[Neon22's Inkscape to OpenSCAD converter](http://www.thingiverse.com/thing:1065500)|
|[Desmos math calculator/plotter](https://www.desmos.com/calculator)|
|[Define/draw Bezier curve w/ desmos](https://www.desmos.com/calculator/cahqdxeshd)|

| $ **Libs** |
|------------------|
|[Brendan M. Sleight's lasercut](https://github.com/bmsleight/lasercut)|
|[Hans Loeblich's functional](https://github.com/thehans/FunctionalOpenSCAD/blob/master/functional.scad) ([discussion](http://forum.openscad.org/Functional-OpenSCAD-working-with-vertex-data-td21080.html)) |
|[Carl Davidson's Relativity](https://github.com/davidson16807/relativity.scad/wiki) |

| $ **Lib systems** |
|------------------|
| [Roya Sutton's odml](http://forum.openscad.org/Doxygen-openscad-amu-and-omdl-Documenting-and-Design-Flow-td19924.html) [pdf](https://cdn.thingiverse.com/assets/3c/16/d2/00/ea/refman.pdf)|
| [Jonathan Law's JointSCAD](https://github.com/HopefulLlama/JointSCAD) |
| [Justin Lin's dotSCAD](https://github.com/JustinSDK/dotSCAD) |
| [Revar Desmera's Belfry OpenScad Library](https://github.com/revarbat/BOSL) |

| $ **OpenSCAD variations** | 
| ----------------------------------------|
| [openjscad](http://www.openjscad.org/) |
| [ImplicitCad (ExtOpenScad)](http://www.implicitcad.org/examples/twisted_extrusion) |
| [OpenSCAD on rollApp](https://www.rollapp.com/launch/openscad) | 
| [OpenSCAD on AWS](http://forum.openscad.org/Running-OpenSCAD-on-an-Amazon-AWS-EC2-server-td9544.html)([pdf](http://files.openscad.org/public/OpenSCAD%20on%20EC2.pdf)) |
| [OpenPyScad](https://github.com/taxpon/openpyscad)|
| [SolidPython](https://github.com/SolidCode/SolidPython) |

|$ **Other cads**| 
|------------------|
|[blockscad](https://blockscad.einsteinsworkshop.com/)|
|[freeCAD](https://www.freecadweb.org/)|
|[snapSCAD](https://github.com/martymcguire/snapscad)|
|[3DDoctors.net](http://3ddoctors.net/)|
|[libfive](https://libfive.com/studio/)|

|$ **Other Drawing programs**| 
|------------------|
|[Context-free](https://github.com/MtnViewJohn/context-free)|

|$ **Other portals** |
|---------------------|
|[shapeoko.com](http://www.shapeoko.com/wiki/index.php/OpenSCAD#Other_Support_Tools)|
|[Fablab](http://fablabamersfoort.nl/book/openscad)|
|[William Adams](http://www.shapeoko.com/wiki/index.php/Programmatic_G-Code_Generators)|

|$ **Inspiration** |
|---------------------|
|[Santos's js 2d/3d transform lib](https://github.com/ruisoftware/jquery-rsSlideIt)|
|[Bending](https://en.wikipedia.org/wiki/Bending)|

|$ **References** |
|---------------------|
| Math: [R.Penner's Easing func](http://robertpenner.com/easing/) |
| Geometry: [2d collision detect in js](https://github.com/bmoren/p5.collide2D/blob/master/p5.collide2d.js) |


[$](http://forum.openscad.org/mailing_list/MailingListOptions.jtp?forum=1) *Runsun Pan, PhD* 
