# CS 2341 - Data Structures Final Project
Search Engine written by Maria Harrison and Landon Wood

In this project, I implemented a search engine along with my partner, Landon Wood. It is a rudimentary search engine, designed to comb through a number of COVID-19 research articles, constructing an inverted file index (stored as an AVL tree) and a hash table to store information about an article's author. The user can then input queries using simple boolean operators to find documents that contain specific words. The engine also writes and saves persistence files; upon execution, if persistence files exist within the directory from a previous execution, then the engine can load those for faster construction of the two main data structures. The engine also records several statistics, such as the number of unique articles indexed, the average words indexed per article, etc.

I wrote the following classes:

- InvertedIndexEntry:
  - Stores a string that is the word and a vector pair of strings and ints that are the documents associated with the word
  - Returns index word and set of documents associated with the indexed word
  - Adds a document to the vector of documents
  - Checkss if a document is in the vector of documents
  - Increases document's frequency if a document is added more than once
  - Returns the total number of times a word appears in all documents

- Node: templated class to act as the node of the AVLTree class
 - Stores data, height, value, pointer to left child, and pointer to right child
 - Follows rule of three by including copy constructor, overloaded assignment operator, and destructor

- AVLTree: templated class
  - Stores the root node, the size of the tree, and a vector of nodes
  - Inserts a node by recursively calling insert while balancing the tree depending on the cases
  - Checks if a value is in the tree by returning true or false
  - Finds and returns the data in a node depending on the given parameter of the value
  - Deletes all nodes from tree and sets root to nullptr

- InvertedIndex:
  - Stores an AVL tree where the data is an InvertedIndexEntry and the value is a string
  - Add a word to the inverted index with its associated document
  - Returns the documents associated with a word in the index
  - Returns number of nodes in the tree
  - Finds and returns top 50 most frequent words in the index

- QueryProcesser:
 - Stores the query as a string, the total number of documents indexed as an int, and a vector of pairs of strings and ints that store the weight of the documents
 - Processes a query entered by the user and returns the 15 most relevant documents based on term frequency-inverse document frequency
  - Parses query to find simple boolean prefixes and stores the keywords associated with the corresponding boolean prefix
  - Stems the keywords to avoid prefixes and suffixes before appending them to individual vectors associated with each boolean prefix

Doxygen-generated documentation is saved under the Documentation folder as `index.html` 
UML Class Diagram is saved in source directory as `Search Engine UML Class Diagram.jpg`
