# Step 5: Data Streaming with Rust

+   1. Implement Data Streaming:

+   2. Write Rust code to stream data using a WebSocket:

```
'''rust use tokio::net::TcpListener; use tokio::prelude::*;
async fn handle_connection(mut socket: tokio::net::TcpStream) {
    let mut buf = [0; 1024];
    loop {
        let n = match socket.read(&mut buf).await {
            Ok(n) if n == 0 => return,
            Ok(n) => n,
            Err(e) => {
                println!("failed to read from socket; err = {:?}", e);
                return;
            }
        };

        if let Err(e) = socket.write_all(&buf[0..n]).await {
            println!("failed to write to socket; err = {:?}", e);
            return;
        }
    }
}

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let addr = "127.0.0.1:8080".to_string();
    let mut listener = TcpListener::bind(addr).await?;

    loop {
        let (socket, _) = listener.accept().await?;
        tokio::spawn(async move {
            handle_connection(socket).await;
        });
    }
}
```