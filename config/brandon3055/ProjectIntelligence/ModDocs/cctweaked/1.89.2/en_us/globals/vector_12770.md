vector
A basic 3D vector type and some common vector operations. This may be useful when working with coordinates in Minecraft's world (such as those from the gps API).

An introduction to vectors can be found on Wikipedia.

Changes
New in version 1.31
new(x, y, z)	Construct a new Vector with the given coordinates.
new(x, y, z)
Source
Construct a new Vector with the given coordinates.

Parameters
x number The X coordinate or direction of the vector.
y number The Y coordinate or direction of the vector.
z number The Z coordinate or direction of the vector.
Returns
Vector The constructed vector.
Types
 Vector
A 3-dimensional vector, with x, y, and z values.

This is suitable for representing both position and directional vectors.

Vector:add(o)
Source
Adds two vectors together.

Parameters
o Vector The second vector to add.
Returns
Vector The resulting vector
Usage
Run ᐅv1:add(v2)
Run ᐅv1 + v2
Vector:sub(o)
Source
Subtracts one vector from another.

Parameters
o Vector The vector to subtract.
Returns
Vector The resulting vector
Usage
Run ᐅv1:sub(v2)
Run ᐅv1 - v2
Vector:mul(m)
Source
Multiplies a vector by a scalar value.

Parameters
m number The scalar value to multiply with.
Returns
Vector A vector with value (x * m, y * m, z * m).
Usage
Run ᐅv:mul(3)
Run ᐅv * 3
Vector:div(m)
Source
Divides a vector by a scalar value.

Parameters
m number The scalar value to divide by.
Returns
Vector A vector with value (x / m, y / m, z / m).
Usage
Run ᐅv:div(3)
Run ᐅv / 3
Vector:unm()
Source
Negate a vector

Returns
Vector The negated vector.
Usage
Run ᐅ-v
Vector:dot(o)
Source
Compute the dot product of two vectors

Parameters
o Vector The second vector to compute the dot product of.
Returns
Vector The dot product of self and o.
Usage
Run ᐅv1:dot(v2)
Vector:cross(o)
Source
Compute the cross product of two vectors

Parameters
o Vector The second vector to compute the cross product of.
Returns
Vector The cross product of self and o.
Usage
Run ᐅv1:cross(v2)
Vector:length()
Source
Get the length (also referred to as magnitude) of this vector.

Returns
number The length of this vector.
Vector:normalize()
Source
Divide this vector by its length, producing with the same direction, but of length 1.

Returns
Vector The normalised vector
Usage
Run ᐅv:normalize()
Vector:round([tolerance])
Source
Construct a vector with each dimension rounded to the nearest value.

Parameters
tolerance? number The tolerance that we should round to, defaulting to 1. For instance, a tolerance of 0.5 will round to the nearest 0.5.
Returns
Vector The rounded vector.
Vector:tostring()
Source
Convert this vector into a string, for pretty printing.

Returns
string This vector's string representation.
Usage
Run ᐅv:tostring()
Run ᐅtostring(v)
Vector:equals(other)
Source
Check for equality between two vectors.

Parameters
other Vector The second vector to compare to.
Returns
boolean Whether or not the vectors are equal.
Last updated on 2022-07-16