# TABLE 15.1 Comparative Study on Lightweight Block Ciphers

| Light weight Block Ciphers | General Parameters | Key Size (in bits) | Block Size (in bits) | Number of Rounds | Mode of network | Throughput 100 kHz (Kbps) | Latency (cycles/block) | Hardware Parameters | Power (micwatt) | Gate equivalent (GD lower) | Analysis |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| PRESENT | | 80/128 | 64 | 31 | SPN | 206 | 31 | | 2.20 | 2195 | Side-channel attack, related-key attack, improved differential analysis, Attacks on full round, truncated differential attack |
| TEA | | 128 | 64 | 64 | Feistel | 6.25 | 512 | | 7.00 | 2355 | Equivalent keys attack |
| CLEFIA | | 128/192/256 | 128 | 18/22/26 | Feistel | 39 | 328 | | 2.48 | 2488 | Improbable differential attack on reduced round |