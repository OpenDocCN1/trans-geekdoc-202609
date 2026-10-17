
As discussed in the last section, the `match` statement uses a closure, which is a self-contained and unnamed function. For that reason, everything that is associated with evaluating the `match` statement is inside a `{}` block. But the whole thing is a statement, so it needs to be terminated with a semicolon ( `;` ). The simple case here is if we get an `Ok` back. The pair of structures will be returned into the two identifiers in the `let` statement at the top of the block.

The one case that's going to be problematic is if, for some reason, the two `UnixStream` structures can't be set up. This is going to result in an `Err`, as we've seen before. It's the implications for the rest of the problem that are problematic. If the IPC streams aren't going to be available, there is no reason to continue with the rest of the program. This means we need to exit the program if this error condition ever occurs. We could just do the panic call as we did before, but this time, the program should just exit with an error code. Of course, rather than just dumping the program, it would be helpful to print an error so the user knows what has happened. The error is in the `println!` statement, and you'll see that the parameter that gets passed into `println!` is the identifier *`e`*. This is the error structure that results from the failed call. We want to print that out in its raw form, so again, we're going to use the debug formatting.

The exit is a call into the `std` crate. It's a simple call, and if you are familiar with writing C or even other similar languages, you may be familiar with it. We're going to follow the Unix convention of returning a non-zero value for an error. Since it's what I'm used to, I'm going to use a –1 because it makes a good error value, being negative. You can feel free to return any non-zero value you like. The non-zero part is important since some operating systems keep track of what the return value from the program is and will provide an indication of abnormal failure if the return value is non-zero.

### Cryptographic Hashing

Part of what we are going to be doing in the next section is performing a cryptographic hash on the contents of a file. It's important to note that the hash is calculated on the contents of a file. This is always the case. You can change the name of the file, the date and time stamp, and permissions on it, and the hash value for the file will remain the same. This will be true of our program as well. The hash is going to be calculated on whatever data happens to be in the file. So, before we talk about generating the hash value, we should spend a short stretch here talking about what a cryptographic hash actually is and what it is valuable for.

The value is really easy to talk about. Depending on the depth we go to, what it is can be very detailed and complicated. So, we'll start with the hash value. As noted, it is based on the contents of a file or a string or basically any data you would like to toss into the hashing algorithm. No matter how many times you run that same data through the hashing algorithm, you will get the same fixed-length value. The length of that value is determined entirely by the algorithm used. Because the value never changes, you can use it for two purposes. The first is making sure one file has exactly the same contents as a second file. This is especially valuable with binary-based files like executables because it's otherwise, at a minimum, time-consuming to do that verification.

The thing about the algorithms used for these hashes is there is no direct correlation between the input data and the output hash, which means the input can't be reversed based on the hash value. Just to demonstrate that point, you can see two hash values shown next. The first is based on the two characters *H* and *i* together. In bytes, that would be the values 48 and 69 in hexadecimal. The second character pair is 48 and 68. You'll see there is a single bit of difference because we've subtracted 1 from the second byte in the first example to get the second byte in the second example. That single bit of difference generates an entirely different value in the hash:

```
kilroy@cutter:/mnt/c/Apps/Cmder$ echo 'Hi' | md5sum
31ebdfce8b77ac49d7f5506dd1495830  -
kilroy@cutter:/mnt/c/Apps/Cmder$ echo 'Hh' | md5sum
747991f32c850b279da5c1e0f68efb95  -
kilroy@cutter:/mnt/c/Apps/Cmder$
```

The second thing we can use a hash value for is to make sure something hasn't changed. You might use this if you were encrypting data and then transmitting it. If you wanted to verify the received value against the transmitted value, you could get a cryptographic hash before you sent and then verify the hash on receipt. This hash value is commonly called a *message authentication code* (MAC). We use the same hash algorithms, or at least we can, for both file hashing as well as message authentication codes.

There are a small number of cryptographic hash algorithms that are commonly used. These are complex mathematical formulas that we aren't going to go into here. You've already seen Message Digest 5 (MD5). A *digest* is another word for a hash value. The problem with MD5 is that it's short. There are only 128 bits in the output of an MD5 hash. While that seems like a lot, it's only 3.4 × 10^38 values. Sure, that may seem like a lot to you, but think about how many different data sets we'd want to generate hash values for. The moment we have two sets of data inputs that generate the same output, we have something called a *collision*, and the more collisions we can generate, the more potential there is for manipulating data that looks like it's valid when it's actually not.

The Secure Hash Algorithm 1 (SHA-1) is a replacement algorithm for MD5. It uses 160 bits rather than 128. While this is only 32 more bits, which might not seem like a lot, remember that with bits, we are talking about powers of 2—so 32 additional bits is actually several orders of magnitude more potential values over MD5. However, what we will be using shortly is SHA-256, meaning we'll be using 256 bits for the result of our hashing. That may be only twice as many bits, but the number of potential values we get is far more than two times the MD5 values. We end up with 1.15 × 10^77 potential values.

### Creating Threads

We're in the final stretch here, so we're going to take a look at the last part of the program; but we're going to start by taking a quick look at the last part first because it's the easiest to deal with. Remember that when we declared the `main` function, we indicated it was going to return a `Result`. This means at some point we need to return an `Ok` result in the case that the program is successful. We've already taken care of the case of returning from the program with an error, although we will have the potential for an additional error coming up in a moment. The very last line in our `main` function is going to be `Ok`, so we return the `Result` the way we are supposed to. This is not a requirement for all programs, but you'll be able to do this at any point you like. Remember that `Ok` contains a value. We don't need a value, so we're just going to pass in a null set.

```
    let serv_handle = thread::spawn( || { sock_server(side1) });
    for file in get_files(&current_dir) {
        let entry = file.unwrap();
        if let Ok(file) = read_file(&entry) {
            let msg = format!("{} : {:x}", entry.path().to_str().unwrap(), Sha256::digest(file.as_bytes()));
            side2.write_all(&msg.into_bytes());
        }
    }
 
    Ok(())
}
```
