![](bbox=[0.135, 0.087, 0.703, 0.531])

**FIGURE 7.42**  Running LinPEAS on a Linux machine.

If we are feeling particularly advanced, we can compile our own versions of PEASS as an obfuscated version of the source code. This helps reduce the chance that it will be detected by Windows Defender and creates a higher likelihood of evading Endpoint Detection and Response (EDR) tools. The PEASS project has a specific page dedicated to compiling an obfuscated version of the tool.

Along with this, there are additional parsing tools that can take the PEASS output and create JSON, HTML, and PDFs of the data generated. To convert the PEASS output from text to PDF, we must convert the text output to JSON first. There are tools within the PEASS-ng repository to help us achieve this objective. Within the **parsers** folder, there are a set of python scripts that can convert the text-based output. Keep in mind however that we must save the output from the script before we can import it – we can achieve this by redirecting the STDOUT to a file with the `>` character. To save the output to a file, we can redirect it using a command similar to below. To view the output as it is generated, we can also use the `tee` command to save it to a file and view it as it is generated.

```
```bash
./linpeas.sh > linpeas.out        # Save output to file
./linpeas.sh | tee linpeas.out     # Save output to file and see it
```
```

Once the program has finished, we will use the **peas2json.py** program to convert the PEASS text-based output to JSON. We call this program with the name of the saved text file and the output file.

```
```bash
python3 peas2json.py </path/to/executed_peass.out> </path/to/peass.json>
python3 peas2json.py ~/linpeas.out linpeas.json
```
```