## Environment Setup
- **Spark Version**: 3.5.3
- **Cluster Manager**: YARN
- **Application Name**: PySparkShell

---

## Commands and Their Functionalities

| Command | Functionality |
|---------|---------------|
| `cd tmp` and `vi inputhdfsdbz.txt` | Create input file locally |
| `hadoop fs -put inputhdfsdbz.txt /tmp/` | Upload file to HDFS NameNode |
| PySpark Read and Transformations | Read file from HDFS and perform Word Count using flatMap, map, reduceByKey |

---

Input Data (List of Sentences):
--------------------------------
[
  "apple banana apple",
  "banana orange banana",
  "apple orange orange",
  "banana apple orange"
]

Stage 1: RDD - Parallelize the Data
-----------------------------------
RDD:
["apple banana apple",
 "banana orange banana",
 "apple orange orange",
 "banana apple orange"]

Stage 2: flatMap - Split Sentences into Words
---------------------------------------------
["apple", "banana", "apple",
 "banana", "orange", "banana",
 "apple", "orange", "orange",
 "banana", "apple", "orange"]

Stage 3: map - Transform into (word, 1)
---------------------------------------
[("apple", 1), ("banana", 1), ("apple", 1),
 ("banana", 1), ("orange", 1), ("banana", 1),
 ("apple", 1), ("orange", 1), ("orange", 1),
 ("banana", 1), ("apple", 1), ("orange", 1)]

Stage 4: reduceByKey - Sum Up Occurrences
-----------------------------------------
[("apple", 4), ("banana", 4), ("orange", 4)]

Final Output:
-------------
[('apple', 4), ('banana', 4), ('orange', 4)]
