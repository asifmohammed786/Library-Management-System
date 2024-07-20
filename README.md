import java.util.ArrayList;
import java.util.List;


class Book {
    private String title;
    private String author;
    private String isbn;

    public Book(String title, String author, String isbn) {
        this.title = title;
        this.author = author;
        this.isbn = isbn;
    }

    public String getTitle() { return title; }
    public String getAuthor() { return author; }
    public String getIsbn() { return isbn; }

    @Override
    public String toString() {
        return "Book{" +
               "title='" + title + '\'' +
               ", author='" + author + '\'' +
               ", isbn='" + isbn + '\'' +
               '}';
    }
}

class User {
    private String name;
    private int userId;

    public User(String name, int userId) {
        this.name = name;
        this.userId = userId;
    }

    public String getName() { return name; }
    public int getUserId() { return userId; }

    @Override
    public String toString() {
        return "User{" +
               "name='" + name + '\'' +
               ", userId=" + userId +
               '}';
    }
}

class Library {
    private List<Book> books;
    private List<User> users;

    public Library() {
        books = new ArrayList<>();
        users = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }

    public void removeBook(String isbn) {
        books.removeIf(book -> book.getIsbn().equals(isbn));
    }

    public Book searchBook(String title) {
        for (Book book : books) {
            if (book.getTitle().equalsIgnoreCase(title)) {
                return book;
            }
        }
        return null;
    }

    public void addUser(User user) {
        users.add(user);
    }

    public void displayBooks() {
        for (Book book : books) {
            System.out.println(book);
        }
    }

    public void displayUsers() {
        for (User user : users) {
            System.out.println(user);
        }
    }
}

public class LibraryManagementSystem {
    public static void main(String[] args) {
        Library library = new Library();

        Book book1 = new Book("The Great Gatsby", "F. Scott Fitzgerald", "12345");
        Book book2 = new Book("1984", "George Orwell", "67890");

        library.addBook(book1);
        library.addBook(book2);

        User user1 = new User("Alice", 1);
        User user2 = new User("Bob", 2);

        library.addUser(user1);
        library.addUser(user2);

        System.out.println("All Books:");
        library.displayBooks();

        System.out.println("\nAll Users:");
        library.displayUsers();

        System.out.println("\nSearching for '1984':");
        System.out.println(library.searchBook("1984"));

        library.removeBook("12345");

        System.out.println("\nAll Books after removal:");
        library.displayBooks();
    }
}
