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
