distinguish between 256 different values—so far, so good. However, we’ll be dealing with values that are significantly larger or smaller than our normal experience. I want you to be able to connect with these values.

We need to deal with SI prefixes. SI is short for the International Standard of scientific abbreviations—but, coming from a Romance language, the adjective is after the noun, so the IS is swapped. The prefixes that are important for us are in Table 3.2. Remember that the exponent is the x in 10^x; it’s also the number of “padded zeros” on the right. That is, kilo means 10^3 = 1000 and 1000 has three zeros on the right. The examples are distances that would be reasonable to measure, using that prefix, applied to meters.

Table 3.2 SI prefixes and length scale examples.

| Prefix | Verbal | Exponent | Example Distance |
|---|---|---|---|
| T | tera | 12 | orbit of Neptune around the Sun |
| G | giga | 9 | orbit of the Moon around the Earth |
| M | mega | 6 | diameter of the Moon |
| K | kilo | 3 | a nice walk |
|  |  | 0 | 1 meter ~ 1 step |
| m | milli | -3 | mosquito |
| μ | micro | -6 | bacteria |
| n | nano | -9 | DNA |

There is another complicating factor. Computers typically work with base-2 amounts of storage, not base-10. So, instead of 10^x we deal with 2^x. Strictly speaking—and scientists are nothing if not strict—we need to account for this difference. For memory, we have some additional prefixes (Table 3.3) that you’ll see in use soon.

Table 3.3 SI base-two prefixes and memory scale examples.

| Prefix | Verbal Prefix | Number of Bytes | Example |
|---|---|---|---|
| KiB | kibi | 2^10 | a list of about 1000 numbers |
| MiB | mebi | 2^20 | a short song as an MP3 |
| GiB | gibi | 2^30 | a feature-length movie |
| TiB | tebi | 2^40 | a family archive of photos and movies |

So, 2 MiB is two mebi-bytes equal to 2^20 bytes. You’ll notice that the base-2 prefixes are also pronounced differently. Ugh. You might wonder why these step up by 10s, not by 3s as in the base-10 values. Since 2^10 = 1024 ~ 1000 = 10^3, multiplying by ten 2s is fairly close to multiplying by three 10s. Unfortunately, these binary prefixes, defined by large standards bodies, haven’t necessarily trickled down to daily conversational use. The good news is that within one measuring system, you’ll probably only see MiB or MB, not both. When you see MiB, just know that it isn’t quite MB.