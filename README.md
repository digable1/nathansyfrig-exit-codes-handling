# parallel-ssh with enhanced exit-codes-handling

Adds an option to handle expected non-zero exit codes that a remote may return.

**-c** exitcodes-file

**--exit-codes** exitcodes-file

<p>Optional file containing expected exit codes or ranges. If specified and the pssh exit code is not 1 - 4, the given file will be read for exit codes, in order specified. If there is any exit code from a remote command that matches exit code specified on the line in file, the status code returned by pssh is 200 plus the line number of the expected exit code that matched. For example, if any exit code from a remote command matches line 2 of the exitcodes-file, the exit code returned by pssh is 202. If there is no match or the exitcodes-file is not specified, pssh does not modify its current behavior for returning exit codes.</p> 

<p>Each line of the exitcodes-file can have one of the following formats and are evaluated in the order encountered in the file:</p>
<ul>
        <li>A single exit code: Example: 3.</li>
        <li>A comparison specification and an exit code: The comparisons are >, >=, <, and <=. Example: >= 20.</li>
        <li>A range, which consists of the following: A greater than comparison (>, >=), an exit code floor, a less than comparison (<, <=), and a ceiling exit code. Example: > 10 <= 15.</li>
</ul>
