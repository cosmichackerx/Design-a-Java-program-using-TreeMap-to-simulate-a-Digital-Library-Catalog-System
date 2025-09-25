# Design-a-Java-program-using-TreeMap-to-simulate-a-Digital-Library-Catalog-System
```java
import java.util.Map;
import java.util.TreeMap;
import java.util.HashMap;
import java.util.Random;

/**
 * A Java program to simulate a Digital Library Catalog System
 * using a TreeMap. This program demonstrates various TreeMap
 * functionalities, compares it with a HashMap, and uses
 * the 'var' keyword and common Map interface methods.
 */
public class DigitalLibraryCatalog {

    public static void main(String[] args) {

        // The 'var' keyword automatically infers the type as TreeMap<Integer, String>.
        // This is a concise way to declare local variables.
        var libraryCatalog = new TreeMap<Integer, String>();

        Random random = new Random();

        // 1. Add Items: Insert at least 6 books with random IDs.
        // TreeMap automatically sorts entries based on the natural order of keys (Integer).
        System.out.println("1. Adding books to the catalog with random IDs...");
        for (int i = 0; i < 6; i++) {
            int bookId = random.nextInt(1000) + 1; // Generate a random ID between 1 and 1000
            String bookTitle = "Book Title " + (char) ('A' + i);
            libraryCatalog.put(bookId, bookTitle);
            System.out.println("  Added: ID " + bookId + ", Title: " + bookTitle);
        }
        System.out.println("\nCatalog after adding books (automatically sorted by ID):");
        System.out.println(libraryCatalog);

        // 2. Access an Item: Retrieve a book title when given its ID.
        System.out.println("\n2. Accessing a book by ID...");
        // Get the first key from the sorted set to ensure it exists
        int firstBookId = libraryCatalog.firstKey();
        String bookTitle = libraryCatalog.get(firstBookId);
        System.out.println("  The title for Book ID " + firstBookId + " is: \"" + bookTitle + "\"");

        // 3. TreeMap Size: Display the total number of books.
        System.out.println("\n3. Current number of books in the catalog: " + libraryCatalog.size());

        // 4. Loop Through a TreeMap: Demonstrate iterating through keys, values, and entries.
        System.out.println("\n4. Looping through the TreeMap...");

        // Print all Book IDs (keys)
        System.out.println("  - All Book IDs (Keys):");
        for (Integer id : libraryCatalog.keySet()) {
            System.out.print(id + " ");
        }

        // Print all Book Titles (values)
        System.out.println("\n\n  - All Book Titles (Values):");
        for (String title : libraryCatalog.values()) {
            System.out.print("\"" + title + "\" ");
        }

        // Print both Book IDs and Titles (entries)
        System.out.println("\n\n  - All Book IDs and Titles (Entries):");
        for (Map.Entry<Integer, String> entry : libraryCatalog.entrySet()) {
            System.out.println("    ID: " + entry.getKey() + ", Title: \"" + entry.getValue() + "\"");
        }
        System.out.println("  Note: The iteration order is always in ascending order of the keys.");

        // 5. TreeMap vs HashMap: Demonstrate the difference in sorting.
        System.out.println("\n5. Comparing TreeMap vs HashMap...");
        var hashMapCatalog = new HashMap<Integer, String>();
        // Add the same books to the HashMap
        for (Map.Entry<Integer, String> entry : libraryCatalog.entrySet()) {
            hashMapCatalog.put(entry.getKey(), entry.getValue());
        }
        System.out.println("  TreeMap (sorted): " + libraryCatalog);
        System.out.println("  HashMap (unsorted): " + hashMapCatalog);
        System.out.println("  Conclusion: A TreeMap is better when you need key-based ordering, while a HashMap is faster for simple key-value storage without any specific order.");

        // 6. Map Interface Methods:
        System.out.println("\n6. Demonstrating common Map interface methods...");

        // containsKey()
        System.out.println("  - Checking if a book ID exists:");
        boolean contains100 = libraryCatalog.containsKey(100);
        System.out.println("    Does catalog contain ID 100? " + contains100);
        int randomId = libraryCatalog.firstKey();
        boolean containsRandomId = libraryCatalog.containsKey(randomId);
        System.out.println("    Does catalog contain ID " + randomId + "? " + containsRandomId);

        // containsValue()
        System.out.println("  - Checking if a book title exists:");
        boolean containsTitle = libraryCatalog.containsValue("Book Title A");
        System.out.println("    Does catalog contain \"Book Title A\"? " + containsTitle);
        boolean containsNonExistent = libraryCatalog.containsValue("Non-existent Title");
        System.out.println("    Does catalog contain \"Non-existent Title\"? " + containsNonExistent);

        // replace()
        System.out.println("  - Replacing a book title:");
        String oldTitle = libraryCatalog.get(randomId);
        libraryCatalog.replace(randomId, "New Updated Title");
        System.out.println("    Updated title for ID " + randomId + " from \"" + oldTitle + "\" to \"" + libraryCatalog.get(randomId) + "\"");

        // 7. Remove Items:
        System.out.println("\n7. Removing items from the catalog...");

        // Remove a specific book by ID
        int keyToRemove = libraryCatalog.lastKey();
        String removedTitle = libraryCatalog.remove(keyToRemove);
        System.out.println("  - Removed book with ID " + keyToRemove + " and title \"" + removedTitle + "\"");
        System.out.println("  Catalog after removal: " + libraryCatalog);

        // Demonstrate clear() to remove all books
        System.out.println("\n  - Using clear() to remove all books...");
        libraryCatalog.clear();
        System.out.println("  Catalog after clear(): " + libraryCatalog);
        System.out.println("  Final size of the catalog: " + libraryCatalog.size());
    }
}
```

---

# 📚 DigitalLibraryCatalog – Java TreeMap & HashMap Demonstration

This Java program simulates a **Digital Library Catalog System** using the **`TreeMap`** class. It demonstrates how books (with randomly generated IDs) can be stored, retrieved, updated, and removed in a catalog. The program also compares **`TreeMap`** with **`HashMap`**, showcasing their differences in ordering and performance, while using common **Map interface methods**.

---

## 🚀 Features Demonstrated

### 1. **Adding Books (TreeMap)**
- Inserts at least 6 books with **random IDs**.  
- `TreeMap` automatically sorts entries by **ascending order of keys** (book IDs).  
- Demonstrates the use of the **`var` keyword** for concise variable declarations.  

---

### 2. **Accessing Books**
- Retrieves a book title by its ID using `get(key)`.  
- Uses `firstKey()` and `lastKey()` to access boundary elements in the catalog.  

---

### 3. **Catalog Size**
- Displays the total number of books using `size()`.  

---

### 4. **Iterating Through the Catalog**
- Iterates over:
  - **Keys** (`keySet()`) → Book IDs.  
  - **Values** (`values()`) → Book Titles.  
  - **Entries** (`entrySet()`) → ID–Title pairs.  
- Demonstrates that iteration order in `TreeMap` is always **sorted by keys**.  

---

### 5. **TreeMap vs HashMap**
- **TreeMap** → Sorted by keys, useful when ordering matters.  
- **HashMap** → Unordered, faster for simple key–value storage.  

**Example Output:**  
```
TreeMap (sorted): {101=Book Title A, 205=Book Title B, 450=Book Title C}
HashMap (unsorted): {205=Book Title B, 101=Book Title A, 450=Book Title C}
```

---

### 6. **Common Map Methods**
- `containsKey()` → Check if a book ID exists.  
- `containsValue()` → Check if a book title exists.  
- `replace()` → Update a book’s title.  

---

### 7. **Removing Books**
- `remove(key)` → Removes a specific book by ID.  
- `clear()` → Removes all books from the catalog.  

---

## 📊 Summary Table

| Feature            | TreeMap                          | HashMap                     |
|--------------------|----------------------------------|-----------------------------|
| **Ordering**       | Sorted by keys (ascending)       | No guaranteed order         |
| **Null Keys**      | ❌ Not allowed                   | ✅ One null key allowed      |
| **Performance**    | O(log n) for operations          | O(1) average for operations |
| **Use Case**       | When sorted order is required    | When speed is more important|

---

## 🎯 Learning Outcomes
- Understand how to use **TreeMap** for sorted key–value storage.  
- Compare **TreeMap vs HashMap** in terms of ordering and performance.  
- Practice **CRUD operations** (Create, Read, Update, Delete) on a catalog system.  
- Learn how to use **Map interface methods** (`containsKey`, `containsValue`, `replace`, `remove`, `clear`).  
- See how the **`var` keyword** simplifies variable declarations in Java 10+.  

---

👉 This program is ideal for students and beginners exploring the **Java Collections Framework**, especially when learning about **Maps** and their real-world applications like digital catalogs, directories, and inventory systems.  

---
