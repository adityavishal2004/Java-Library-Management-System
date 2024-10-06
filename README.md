# Java-Library-Management-System
import java.util.ArrayList;
import java.util.Scanner;

class Book {
    String title, author;
    boolean isBorrowed;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
        this.isBorrowed = false;
    }

    public void borrowBook() {
        isBorrowed = true;
    }

    public void returnBook() {
        isBorrowed = false;
    }

    public String toString() {
        return "Title: " + title + ", Author: " + author + ", Borrowed: " + (isBorrowed ? "Yes" : "No");
    }
}

public class Library {
    private ArrayList<Book> books;

    public Library() {
        books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }

    public void listBooks() {
        for (Book book : books) {
            System.out.println(book);
        }
    }

    public void borrowBook(int index) {
        if (!books.get(index).isBorrowed) {
            books.get(index).borrowBook();
            System.out.println("Book borrowed successfully.");
        } else {
            System.out.println("Book is already borrowed.");
        }
    }

    public void returnBook(int index) {
        if (books.get(index).isBorrowed) {
            books.get(index).returnBook();
            System.out.println("Book returned successfully.");
        } else {
            System.out.println("Book was not borrowed.");
        }
    }

    public static void main(String[] args) {
        Library library = new Library();
        Scanner scanner = new Scanner(System.in);

        library.addBook(new Book("The Great Gatsby", "F. Scott Fitzgerald"));
        library.addBook(new Book("1984", "George Orwell"));

        while (true) {
            System.out.println("\nLibrary Menu:\n1. List Books\n2. Borrow Book\n3. Return Book\n4. Exit");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    library.listBooks();
                    break;
                case 2:
                    System.out.println("Enter book index to borrow: ");
                    int borrowIndex = scanner.nextInt();
                    library.borrowBook(borrowIndex);
                    break;
                case 3:
                    System.out.println("Enter book index to return: ");
                    int returnIndex = scanner.nextInt();
                    library.returnBook(returnIndex);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                default:
                    System.out.println("Invalid option.");
            }
        }
    }
}
