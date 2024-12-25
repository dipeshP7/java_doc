
Java Memory Utilization

** int[] data

When you declare an array like int[] data in Java, the memory usage depends on several factors:

Memory Breakdown
Reference Variable (data):

	data is a reference variable that points to the array object in the heap.
	The reference variable itself is stored in the stack and typically takes 4 bytes on a 32-bit JVM or 8 bytes on a 64-bit JVM 
	(depending on the JVM settings, like the CompressedOops flag).
	
Array Object (in the heap):

	An array in Java is an object. It has:

	Object header:
		which contains metadata like synchronization information and type identification.
	
		On a 32-bit JVM: 8 bytes.
		On a 64-bit JVM with CompressedOops enabled: 12 bytes.
		On a 64-bit JVM without CompressedOops: 16 bytes.
	
	Length field: 4 bytes (to store the size of the array).
	
	The actual memory for the array elements depends on the data type and the size of the array.
	For int, each element takes 4 bytes.
	
Padding:

	To align objects in memory, the JVM may add padding bytes to ensure the total size is a multiple of 8 bytes.
	Formula for Total Memory Used by int[]

	Total Memory = Object Header + Length Field+ (Number of Elements)× Size of Each Element + Padding

Example
If you declare int[] data = new int[10];:

Object Header: 12 bytes (assuming 64-bit JVM with CompressedOops).
Length Field: 4 bytes.
Array Elements: 10× 4 bytes=40 bytes

Padding: To align to 8 bytes, total = 12+4+40=56, already a multiple of 8, so no padding.
Total Memory: 56 bytes for the array object, plus 4 or 8 bytes for the reference variable.

--------------------------------------------------------------------------------

