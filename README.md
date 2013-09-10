VisDock
=======

VisDock Libraries
----------------------------------------------------------------------------------------------------
VisDock is an interactive web-visualization framework written in JavaScript. VisDock allows visualization
creators to import various VisDock tools into their host visuailzations for exploration and annotation
purposes.

### VisDock.js
VisDock.js library contains various tools: such tools include cross-cutting selection tools,
pan/zoom tool, query management tools, and annotation tools. VisDock can be imported into any SVG
rendered visualizations.

### 2D.js and IntersectionLibrary.js
These libraries provide functions to determine whether the user-drawn shapes or lines cross the
boundaries of SVG objects. These files were obtained from Kevin Lindsey Software Development
(www.kevlindev.com). Cross-cutting selections can be made between:
- Path and Polygon
- Path and Elllipse
- Path and Line
- Polygon and Polygon
- Polygon and Ellipse
- Polygon and Line
- Ellipse and Ellipse
- Ellipse and Line
- Line and Line

### visdock.utils.js
2D.js and IntersectionLibrary.js provide functions to determine the intersection of any two SVG objects. For
VisDock.js users, the type of intersection is limited to between user-drawn shapes (polygons, ellipses, and
lines) and SVG objects in the host visualization. visdock.utils.js summarizes these intersections in a
more compact form.

#### Functions for Initializations and Sub-classes
Once the users have drawn a shape using Polygon, Lasso, or Rectangle tool, the array of 
the x and y coordinates of the verticies will be passed to the VisDock event handler. This array cannot 
be used directly for the verification of intersection because the 2D.js and IntersectionUtilities.js libraries require
specific object formats. The following functions initialize path, polygon, ellipse, and line elements 
from the 
In order to check the intersection between shapes, it may require to initialize the shapes as
an SVG shape class before passing them as argument. Here are the functions that initialize such shapes.
But note that not all shapes need to be initialized. We will explain further when an object needs to be
initialized.
  - createPolygon (points): initializes a polygon object created when Lasso, Polygon, and Rectangle selections
are made.
<br>
<pre><code>var NewPolygon = new createPolygon(points)
</code></pre>
    + points: when the users use Lasso, Polygon, and Rectangle tools, VisDock stores an array of points
for the lasso, polygon, and rectangle in the array form [[x1, y1], [x2, y2], [x3, y3], ... , [xn, yn]].<br>
    + Sub-classes: its sub-classes are used to verify intersection between NewPolygon and any SVG object.
<ul>
     <li> NewPolygon.intersectPath(path, inclusive): checks the inclusive/exclusive intersection between
NewPolygon and an SVG path element.
     <li> NewPolygon.intersectPolygon(polygon, inclusive): checks the inclusive/exclusive intersection
between NewPolygon and an SVG polygon element.
     <li> NewPolygon.intersectEllipse(path, inclusive): checks the inclusive/exclusive intersection
between NewPolygon and an SVG ellipse element.
     <li> NewPolygon.intersectLine(path, inclusive): checks the inclusive/exclusive intersection
between NewPolygon and an SVG line element.
</ul>
<br>
  
  - createEllipse (points): initializes an ellipse object created when Ellipse selections are made.
<br>
<pre><code>var NewEllipse = new createEllipse(points)
</code></pre>
    + points: when the users use Ellipse tool, VisDock stores an array of points for such ellipse
in the form [cx, cy, r1, r2]. <br>
    + Sub-classes: its sub-classes are used to verify intersection between NewEllipse and any SVG object.
<ul>
     <li> NewEllipse.intersectPath(path, inclusive): checks the inclusive/exclusive intersection between
NewEllipse and an SVG path element.
     <li> NewEllipse.intersectPolygon(polygon, inclusive): checks the inclusive/exclusive intersection
between NewEllipse and an SVG polygon element.
     <li> NewEllipse.intersectEllipse(path, inclusive): checks the inclusive/exclusive intersection
between NewEllipse and an SVG ellipse element.
     <li> NewEllipse.intersectLine(path, inclusive): checks the inclusive/exclusive intersection
between NewEllipse and an SVG line element.
</ul>
<br>
    
  - createLine (points): initializes a line/polylinee object created when StraightLine, Polyline and Freeselect
selections are made.
<br>
<pre><code>var NewLine = new createLine(points)
</code></pre>
    + points: when the user uses StraightLine, Polyline, and Freeselection tools, VisDock stores an
array of points for such in the form [[x1, y1], [x2, y2], [x3, y3], ... , [xn, yn]]. Note that if the line
is a straight line, the array would contain only 2 elements.
<br>
    + Sub-classes: its sub-classes are used to verify intersection between NewLine and any SVG object.
<ul>
     <li> NewLine.intersectPath(path, inclusive): checks the inclusive/exclusive intersection between
NewLine and an SVG path element.
     <li> NewLine.intersectPolygon(polygon, inclusive): checks the inclusive/exclusive intersection
between NewNew and an SVG polygon element.
     <li> NewLine.intersectEllipse(path, inclusive): checks the inclusive/exclusive intersection
between NewLine and an SVG ellipse element.
     <li> NewLine.intersectLine(path, true): checks the inclusive intersection
between NewLine and an SVG line element (note that there cannot be any exclusive intersection between
a line and another line).
</ul>
<br> 
    
#### Other important functions:
Inside the visdock class are a few important functions that are desgined to aid proper display of the layers. 
The newly created layers have visibility and color attributes. Some of these functions can add/change these
attributes as the users desire.

  - 
   
<a href="https://github.com/jungujchoi/VisDock/blob/master/Tutorials.md">Go to VisDock Tutorials</a>
------------------------------------------------------------------------------------------------------
