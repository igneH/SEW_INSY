## 3. Threads-, Netzwerkprogrammierung und Fehlerbehandlung ##
1. Sockets:
	- Kommunikationsendpunkte, die für die Netzwerkprogrammierung verwendet werden, Übertragung von Daten zwischen zwei Geräten über ein Netzwerk
2. Sockets mit Threads:
	- Multithreading, Server muss für jede Client-Verbindung einen neuen Thread starten um Anfragen parallel zu verarbeiten
3. Threads und Synchronisierung
	- Locks
4. Exceptions
	- try, catch, finally
		- mehrere catch blöcke, von oben nach unten durchgehen

- Server Bsp Code
```Java
public class Server {
    public static void main(String[] args) {
        Socket socket;
        Lock lock = new ReentrantLock();
        ExecutorService executorService = Executors.newCachedThreadPool();

        try (ServerSocket serverSocket = new ServerSocket(8080)) {
            System.out.println("Server connected");

            while (true) {
                socket = serverSocket.accept();
                executorService.execute(new ClientHandler(socket, lock));
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
- ClientHandler Bsp Code
```Java
public class ClientHandler implements Runnable {
    private Socket socket;
    private Lock lock;

    public ClientHandler(Socket socket, Lock lock) {
        this.socket = socket;
        this.lock = lock;
    }

    @Override
    public void run() {
        if (socket != null) {
            try {
                try (DataOutputStream oos = new DataOutputStream(socket.getOutputStream());
                     DataInputStream ois = new DataInputStream(socket.getInputStream())) {
                    System.out.println("connected");

                    while (true) {
                        Object request = ois.readUTF();
                        System.out.println(request.toString());
                        try {
                            lock.lock();
                            // Datenbankzugriff
                            // ...
                            oos.writeUTF("ich habe die Nachricht: "+ request + " erhalten");
                        } finally {
                            lock.unlock();
                        }
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```
- Client Bsp Code
```Java
public class Client {
    public static void main(String[] args) throws IOException {
        Socket serverSocket = new Socket("localhost",8080);
        DataInputStream ois = new DataInputStream(serverSocket.getInputStream());
        DataOutputStream oos = new DataOutputStream(serverSocket.getOutputStream());

        oos.writeUTF("LUL");
        System.out.println(ois.readUTF());
        oos.flush();
    }
}
```