## OpenSCAD snippets for copy and paste ##

| [**hash**( *h,k* )](#hash) | [**Line**( *pts* )](#line) | [**rotate**( *angle* )](#rotate) | [**sortArrs**( *arrs,by=0* )](#sortarrs) |
|--|--|--|--|

---
### hash
| Type | API | Source | Remark |
|------|-----|--------|--------|
|Func| **hash**( *h,k* ) | Runsun | Very efficient search()-based associated array|

```javascript
function hash(h,k, notfound)= 
(
  let(rtn = h[ search([k], [for(i=[0:2:len(h)-2])h[i]])[0]*2+1 ])
  rtn==undef?notfound:rtn
);  

echo( hash( ["a",1,"b",2], "a" ) );  // 1
echo( hash( ["a",1,"b",2], "b" ) );  // 2
echo( hash( ["a",1,"b",2], "c" ) );  // undef
echo( hash( ["a",1,"b",2], "c", "missing" ) ); // "missing"
```

---
### Line

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Module| **Line**( *pts* ) | Inspired by [Ronaldo](http://forum.openscad.org/Can-you-sweep-a-object-with-fingers-tp19057p19330.html) | Much more efficient than a direct hull() of points|

```javascript
module Line( pts, r=0.05, closed=false, color=undef, transp=1, fn=4 )
{
  if(len(pts)>1 && len(pts[0])>1 && r>0) 
  { 
    // Convert to 3d if 2d; Attach 1st pt if closed
    pts  = concat( [for(p=pts) [ p[0],p[1],p[2]==undef?0:p[1] ]],  
                  closed? [[ pts[0][0], pts[0][1], pts[0][2]==undef?0:pts[0][2] ]] : []
    ); 
    color(color,transp)
    for(i=[0:len(pts)-2]) 
    { 
       v = pts[i+1]-pts[i]; 
       L = norm(v); 
       if( L > 1e-12) 
         translate(pts[i]) 
         rotate([0, acos(v[2]/L), atan2(v[1],v[0])]) 
         rotate(45) cylinder(h=L, r=r, $fn=fn); 
    } 
  } 
}        
```


---
### rotate

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **rotate**( *angle* ) | [nophead](http://forum.openscad.org/Rounding-Errors-tp21821p21834.html) | Fix an issue of the built-in rotate()|

```javascript
module rotate(angle)            // built-in rotate is inaccurate for 90 degrees, etc
{
 a = len(angle) == undef ? [0, 0, angle] : angle;
 cx = cos(a[0]);
 cy = cos(a[1]);
 cz = cos(a[2]);
 sx = sin(a[0]);
 sy = sin(a[1]);
 sz = sin(a[2]);
 multmatrix([
  [ cy * cz, cz * sx * sy - cx * sz, cx * cz * sy + sx * sz, 0],
  [ cy * sz, cx * cz + sx * sy * sz,-cz * sx + cx * sy * sz, 0],
  [-sy,      cy * sx,                cx * cy,                0],
  [ 0,       0,                      0,                      1]
 ]) children();
}      
```


--- 
### sortArrs

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **sortArrs**( *arrs,by=0* ) | [runsun](http://forum.openscad.org/Programming-in-Functional-OpenSCAD-tp23039p23280.html) | A quick sort for arrays based on given index. Inspired by [Ronaldo](http://forum.openscad.org/Programming-in-Functional-OpenSCAD-tp23039p23272.html) |

```javascript
function sortArrs(arrs, by=0)=
(
  !(len(arrs)>0) ? [] : 
    let( pivot   = arrs[floor(len(arrs)/2)][by],
           lesser  = [ for (y = arrs) if ( y[by]  < pivot ) y ],                                        ,
           equal   = [ for (y = arrs) if ( y[by] == pivot ) y ] ,
           greater = [ for (y = arrs) if ( y[by]  > pivot ) y ]
       )
      concat( sortArrs(lesser, by), 
              equal, 
              sortArrs(greater, by) 
            )
);

arrs = [[2.9, 1.9, -2.8], [-2.5, -1.5, -2.9], [-0.1, 2.8, 2.4], [0.9, 1.8, 
0.8], [-1, -1.3, -0.8]] ;

sortArrs(arrs,by=0):

 [[-2.5, -1.5, -2.9] 
, [-1, -1.3, -0.8] 
, [-0.1, 2.8, 2.4] 
, [0.9, 1.8, 0.8] 
, [2.9, 1.9, -2.8]] 

sortArrs(arrs,by=1):

[[-2.5, -1.5, -2.9] 
, [-1, -1.3, -0.8] 
, [0.9, 1.8, 0.8] 
, [2.9, 1.9, -2.8] 
, [-0.1, 2.8, 2.4] 
] 

sortArrs(arrs,by=2):

 [[-2.5, -1.5, -2.9] 
, [2.9, 1.9, -2.8] 
, [-1, -1.3, -0.8] 
, [0.9, 1.8, 0.8] 
, [-0.1, 2.8, 2.4]] 

```
