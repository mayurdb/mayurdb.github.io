## Spark3D

Spark3D is as an open-source Spark library to process large scala 3D data-sets from, Astrophysics, High Energy Physics, Meteorology, etc. The library works on top of the latest Spark versions (2.0+), has user friendly APIs (in Scala and Python (ongoing)), works on top of HDFS and supports all major file formats (CSV, Parquet, JSON, Avro, etc.) including popular scientific file formats such as FITS.

## Approach

![Workflow](/assets/img.png)

Step - 1: 
Load the data from the source into a raw RDD and then subsquently mapped to a 3D RDD (Point3DRDD or SphereRDD).

Step - 2:
Partition the 3D space (Octree/Onion partitioning) to map points which are in proximity to one another to a uniquely identifiable region.

Step - 3:
Repartition the RDD with custom Octree or Onion partitioner (based on which partitioning scheme was used in Step-2) to store data points inside the region identified in Step-2 in a unique partition. 

Step - 4:
Index the RDD to reduce the latency of elements access. (optional)

Step - 5:
Apply custom queries (Pixel/Center cross match, Range and KNN) on top of the data.

## Topics worked on - 
1. JTS (a Java library for creating and manipulating 2D vector geometry.) replacement for 3D
   1. Main PR -
      https://github.com/astrolabsoftware/spark3D/pull/22

   2. Bug Fix - 
      https://github.com/astrolabsoftware/spark3D/pull/67

2. Octree
   1. Octree implementation - 
      https://github.com/astrolabsoftware/spark3D/pull/30
    
   2. Octree partitioner - 
      https://github.com/astrolabsoftware/spark3D/pull/36
   
   3. Sample size related fix
      https://github.com/astrolabsoftware/spark3D/pull/56
      
   4. Avoiding driver going OOM(Out of memory issue) issue - 
      https://github.com/astrolabsoftware/spark3D/pull/71

   5. Missing elements after repartitioning fix - 
      https://github.com/astrolabsoftware/spark3D/pull/76
    
3. KNN
   1. KNN Naive - 
      https://github.com/astrolabsoftware/spark3D/pull/59
    
   2. KNN efficient -
      https://github.com/astrolabsoftware/spark3D/pull/60

   3. KNN efficient optimizations - 
      https://github.com/astrolabsoftware/spark3D/pull/62
    
   3. KNN Unique - 
      https://github.com/astrolabsoftware/spark3D/pull/68/files
  
   4. KNN Ordering bug fix - 
      https://github.com/astrolabsoftware/spark3D/pull/80

4. SphereRDD
   1. Main PR - 
      https://github.com/astrolabsoftware/spark3D/pull/38

5. Minor fix -
   https://github.com/astrolabsoftware/spark3D/pull/27
   
## To Do - 
1. Build index to speed-up spatial queries
   
2. RTree partitioning implementation (work in progress)
   https://github.com/astrolabsoftware/spark3D/pull/87

3. Spark3D suppport on S3

### Jekyll Themes
