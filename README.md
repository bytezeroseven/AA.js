
# AA.js
Collision handler for basic axis-aligned shapes. Supports cylinders, spheres, and boxes. That should be sufficient for a small game in my opinion.

See it in action here https://bytezeroseven.github.io/AA.js/

## How to use?
The code provides functions like `shape1IntersectsShape2` to check if the shapes are colliding. If they collide, an object containing the minimum translation vector (mtv) and the minimum distance to separate the objects (minOverlap) is returned. The MTV always points in the direction of shape1.

**Example #1: Detecting and resolving collision between two spheres**

	var intersection = sphereIntersectsSphere( aCenterX, aCenterY, aCenterZ, aRadius, bCenterX, bCenterY, bCenterZ bRadius);
	
	if ( intersection !== false ) {
	
		console.log( 'intersecting' );
		
		var halfOverlap = intersection.minOverlap / 2;
		aCenterX += intersection.mtvX * halfOverlap;
		aCenterY += intersection.mtvY * halfOverlap;
		aCenterZ += intersection.mtvZ * halfOverlap;
		
		bCenterX -= intersection.mtvX * halfOverlap;
		bCenterY -= intersection.mtvY * halfOverlap;
		bCenterZ -= intersection.mtvZ * halfOverlap;
		
	}

Note: As mentioned before, the mtv points in the direction of the first shape (in this case, sphere A). So for moving the other sphere apart we negate the minimum translation vector.

## Documentation

	boxIntersectsBox( aminx, aminy, aminz, amaxx, amaxy, amaxz, bminx, bminy, bminz, bmaxx, bmaxy, bmaxz )
	boxIntersectsSphere( minx, miny, minz, maxx, maxy, maxz, sx, sy, sz, sr );
	boxIntersectsCylinder( minx, miny, minz, maxx, maxy, maxz, cx, cy, cz, ch, cr )
	
	sphereIntersectsSphere( ax, ay, az, ar, bx, by, bz, br )
	sphereIntersectsCylinder( sx, sy, sz, sr, cx, cy, cz, ch, cr )
	sphereIntersectsBox( sx, sy, sz, sr, minx, miny, minz, maxx, maxy, maxz )
	
	cylinderIntersectsCylinder( ax, ay, az, ah, ar, bx, by, bz, bh, br )
	cylinderIntersectsSphere( cx, cy, cz, ch, cr, sx, sy, sz, sr )
	cylinderIntersectsBox( cx, cy, cz, ch, cr, minx, miny, minz, maxx, maxy, maxz )
