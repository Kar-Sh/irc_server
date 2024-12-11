# IRC Server in C++98

## Description
An implementation of an Internet Relay Chat (IRC) server written in C++98. The server supports multiple simultaneous clients, adheres to IRC standards for communication, and implements key channel functionalities, including authentication, nickname, and username setup.

## Key Features
- **Connection:** Handles TCP/IP (IPv4 and IPv6) with a non-blocking architecture.
- **Client Interaction:** Implements authentication, nickname, username, and basic chat functionality.
- **Channel Management:** Includes features for creating channels, forwarding messages, and supporting operators with commands such as `KICK`, `INVITE`, `TOPIC`, and `MODE`.
- **Operator Commands:** Provides channel moderation capabilities:
  - `MODE` flags for invite-only, topic restrictions, password protection, operator privileges, and user limits.
- **Reliability:** Processes partial data, ensures low-bandwidth compatibility, and prevents server hangs.

## Technical Details
- **Standard:** Compliant with C++98, using features like `<cstring>` over C alternatives.
- **Build System:** Includes a `Makefile` with rules for `$(NAME)`, `all`, `clean`, `fclean`, and `re`.
- **Compilation Flags:** `-Wall -Wextra -Werror -std=c++98`
- **Libraries and Functions:** Only standard C++98 and listed functions like `poll`, `recv`, `send`, etc., are used.
- **Testing:** Compatible with standard IRC clients and supports testing with tools like `nc`.

## Usage
To build and run the IRC server:

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Compile the source code using `make`:
   ```bash
   make
   ```

3. Run the server with the following syntax:
   ```bash
   ./ircserv <port> <password>
   ```

   - `<port>`: The port number on which the server will listen for incoming connections.
   - `<password>`: The connection password required by clients.

## Testing
You can use tools like `nc` to test the server. For example:
```bash
nc 127.0.0.1 6667
```
Use `Ctrl+D` to send the command in parts to test the server's ability to handle partial data:
1. Type `com` and press `Ctrl+D`.
2. Type `man` and press `Ctrl+D`.
3. Type `d\n` and press `Enter`.

The server will aggregate received packets to rebuild the command and process it correctly.

---

Feel free to report issues or contribute enhancements to the project!
