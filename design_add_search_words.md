# Design Add and Search Words Data Structure

>Design a data structure that supports adding new words and finding if a string matches any previously added string.

>Implement the WordDictionary class:

- WordDictionary() Initializes the object.
- void addWord(word) Adds word to the data structure, it can be matched later.
- bool search(word) Returns true if there is any string in the data structure that matches word or false otherwise. word may contain dots '.' where dots can be matched with any letter.

## Example:
**Input**
```
["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
```
**Output**
```
[null,null,null,null,false,true,true,true]
```
**Explanation**
```
WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
```


## Dart

```
class WordDictionary {
  // The root node of trie
  late TrieNode root;

  // Initialize your data structure here
  WordDictionary() {
    root = TrieNode();
  }

  // Adds a word into the data structure
  void addWord(String word) {
    TrieNode curr = root; // Start from root node
    for (int i = 0; i < word.length; i++) {
      // Loop through each letter
      final c = word[i]; // Get current letter
      if (!curr.children.containsKey(c)) {
        // If no child node exists for this letter
        curr.children[c] = TrieNode(); // Create a new child node
      }
      curr = curr.children[c]!; // Move to the child node
    }
    curr.isWord = true; // Mark as end of word
  }

  // Returns if the word is in the data structure. A word could contain
  //the dot character '.' to represent any one letter.

  bool search(String word) {
    return _searchHelper(word, root); // Call helper function with root node
  }

  bool _searchHelper(String word, TrieNode node) {
    if (word.isEmpty) {
      // If no more letters to match
      return node.isWord; // Return whether it is end of word
    }

    final c = word[0]; // Get first letter

    if (c == '.') {
      // If it is wildcard character

      for (final TrieNode child in node.children.values) {
        if (_searchHelper(word.substring(1), child)) {
          return true;
        }
      }

      return false;
    } else {
      if (!node.children.containsKey(c)) {
        return false;
      }

      return _searchHelper(word.substring(1), node.children[c]!);
    }
  }
}

// Define a class for TrieNode
class TrieNode {
  // A map of children nodes
  late Map<String, TrieNode> children;
  // A flag to indicate if this node is a word end
  late bool isWord;

  // Constructor
  TrieNode() {
    children = {};
    isWord = false;
  }
}
```