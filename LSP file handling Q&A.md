1.Write a C program to create a new text file and write \"Hello,
World!\" to it?

#include\<stdio.h\> int main() { FILE \*open; Open = fopen("hello", "w"
); fprintf(open,"hello world!"); fclose(open); printf("writint to the
file was successful\\n"); printf("closing the program"); return 0; }

2\. Develop a C program to open an existing text file and display its
contents?

#include \<stdio.h\> #include \<stdlib.h\> void main() { FILE \*fptr;
char fname\[20\]; char str; printf(\"\\n\\n Read an existing file
:\\n\"); printf(\" Input the filename to be opened : \");
scanf(\"%s\",fname); fptr = fopen (fname, \"r\"); if (fptr == NULL) {
printf(\" File does not exist or cannot be opened.\\n\"); exit(0); }
printf(\"\\n The content of the file %s is :\\n\",fname); str =
fgetc(fptr); while (str != EOF) { printf (\"%c\", str); str =
fgetc(fptr); } fclose(fptr); printf(\"\\n\\n\"); }

3\. Implement a C program to create a new directory named \"Test\" in
the current directory?

#include \<stdio.h\> #include \<stdlib.h\> #include \<sys/stat.h\>
#include \<sys/types.h\> int main() { const char \*dirname = \"Test\";
int status = mkdir(dirname, 0777); if (status == 0) { printf(\"Directory
\'%s\' created successfully.\\n\", dirname); } else { perror(\"Error
creating directory\"); return 1; } return 0; }

4\. Write a C program to check if a file named \"sample.txt\" exists in
the current directory?

#include \<stdio.h\> #include \<stdlib.h\> #include \<unistd.h\>
#include \<sys/stat.h\> int main() { const char \*filename =
\"sample.txt\"; struct stat buffer;

if (stat(filename, &buffer) == 0) { printf(\"File \'%s\' exists in the
current directory.\\n\", filename); } else { printf(\"File \'%s\' does
not exist in the current directory.\\n\", filename); }

return 0; }

5.Develop a C program to rename a file from \"oldname.txt\" to
\"newname.txt\"?

#include \<stdio.h\> int main() {

int result = rename(\"oldname.txt\", \"newname.txt\"); if (result == 0)
{ printf(\"File renamed successfully!\\n\"); } else { perror(\"Error
renaming file\"); }

return 0; }

6.Implement a C program to delete a file named \"delete_me.txt\"?

#include \<stdio.h\> int main() { if (remove(\"delete_me.txt\") == 0) {
printf(\"File \'delete_me.txt\' deleted successfully.\\n\"); } else {
perror(\"Error deleting file\"); } return 0; }

7\. Write a C program to copy the contents of one file to another?

#include\<stdio.h\> #include \<stdlib.h\> int main() { FILE
\*sourceFile, \*destinationFile; char sourceFileName\[100\],
destinationFileName\[100\]; int ch; printf(\"Enter the name of the
source file: \"); scanf(\"%s\", sourceFileName); sourceFile =
fopen(sourceFileName, \"r\"); if (sourceFile == NULL) { printf(\"Error
opening source file.\\n\"); return 1; } printf(\"Enter the name of the
destination file: \"); scanf(\"%s\", destinationFileName);
destinationFile = fopen(destinationFileName, \"w\"); if(destinationFile
== NULL) { printf(\"Error opening destination file.\\n\");
fclose(sourceFile); return 1; } while ((ch = fgetc(sourceFile)) != EOF)
{ fputc(ch, destinationFile); } printf(\"File copied
successfully.\\n\"); fclose(sourceFile); fclose(destinationFile); return
0; }

8\. Develop a C program to move a file from one directory to another?

#include \<stdio.h\> #include \<stdlib.h\> #include \<string.h\> int
main() { char sourcePath\[256\]; char destinationPath\[256\];
printf(\"Enter the source file path: \"); scanf(\"%s\", sourcePath);
printf(\"Enter the destination file path: \"); scanf(\"%s\",
destinationPath); if (rename(sourcePath, destinationPath) == 0) {
printf(\"File moved successfully.\\n\"); } else { perror(\"Error moving
file\"); return 1; } return 0; }

9\. Implement a C program to list all files in the current directory?

#include \<stdio.h\> #include \<dirent.h\> #include \<errno.h\> int
main() { DIR \*dir; struct dirent \*ent; dir = opendir(\".\"); // Open
current directory if (dir == NULL) { perror(\"Could not open
directory\"); return 1; } while ((ent = readdir(dir)) != NULL) {
printf(\"%s\\n\", ent-\>d_name); } closedir(dir); return 0; }

10\. Write a C program to get the size of a file named \"file.txt\"?

#include \<stdio.h\> #include \<stdlib.h\> int main() { FILE \*fp; long
size; fp = fopen(\"file.txt\", \"r\"); if (fp == NULL) { printf(\"Error
opening file.\\n\"); return 1; } fseek(fp, 0, SEEK_END); size =
ftell(fp); fclose(fp); printf(\"Size of file.txt: %ld bytes\\n\", size);
return 0; }

11\. Develop a C program to check if a directory named \"Test\" exists
in the current directory?

#include \<stdio.h\> #include \<sys/stat.h\> #include \<sys/types.h\>
int main() { struct stat st; if (stat(\"Test\", &st) == 0) { if
(S_ISDIR(st.st_mode)) { printf(\"Directory \'Test\' exists.\\n\"); }
else { printf(\"\'Test\' exists, but it\'s not a directory.\\n\"); } }
else { printf(\"Directory \'Test\' does not exist.\\n\"); } return 0; }

12\. Implement a C program to create a new directory named \"Backup\" in
the parent directory?

#include \<stdio.h\> #include \<stdlib.h\> #include \<sys/stat.h\>
#include \<sys/types.h\> #include \<errno.h\> int main() { char
\*dirname = \"../Backup int status = mkdir(dirname, 0777); if (status ==
0) { printf(\"Directory \'%s\' created successfully.\\n\", dirname); }
else { if (errno == EEXIST) { printf(\"Directory \'%s\' already
exists.\\n\", dirname); } else { perror(\"Error creating directory\"); }
return 1; } return 0; }

13\. Write a C program to recursively list all files and directories in
a given directory?

#include \<stdio.h\> #include \<stdlib.h\> #include \<string.h\>
#include \<dirent.h\> #include \<sys/stat.h\> void
list_files_recursive(const char \*path) { DIR \*dir; struct dirent
\*ent; struct stat file_stat; char full_path\[1024\];

dir = opendir(path); if (dir == NULL) { perror(\"Could not open
directory\"); return; } while ((ent = readdir(dir)) != NULL) { if
(strcmp(ent-\>d_name, \".\") == 0 \|\| strcmp(ent-\>d_name, \"..\") ==
0) { continue; } snprintf(full_path, sizeof(full_path), \"%s/%s\", path,
ent-\>d_name); if (stat(full_path, &file_stat) == 0) { if
(S_ISDIR(file_stat.st_mode)) { printf(\"Directory: %s\\n\", full_path);
list_files_recursive(full_path); } else { printf(\"File: %s\\n\",
full_path); }

} else { perror(\"Error getting file stat\"); } } closedir(dir); } int
main(int argc, char \*argv\[\]) { if (argc != 2) { fprintf(stderr,
\"Usage: %s \<directory\>\\n\", argv\[0\]); return 1; }
list_files_recursive(argv\[1\]); return 0; }

14\. Develop a C program to delete all files in a directory named
\"Temp\"?

#include \<stdio.h\> #include \<stdlib.h\> #include \<string.h\>
#include \<dirent.h\> #include \<unistd.h\> #include \<sys/stat.h\> int
main() { DIR \*dir; struct dirent \*ent; char dir_name\[\] = \"Temp\";
char file_path\[256\]; dir = opendir(dir_name); if(dir == NULL) {
perror(\"Error opening directory\"); return 1; } while ((ent =
readdir(dir)) != NULL) { if (strcmp(ent-\>d_name, \".\") == 0 \|\|
strcmp(ent-\>d_name, \"..\") == 0) { continue; // Skip current and
parent directories } snprintf(file_path, sizeof(file_path), \"%s/%s\",
dir_name, ent-\>d_name); if (unlink(file_path) == -1) { perror(\"Error
deleting file\"); } else { printf(\"Deleted: %s\\n\", file_path); } }
closedir(dir); if (rmdir(dir_name) == -1) { perror(\"Error removing
directory\"); } else { printf(\"Removed directory: %s\\n\", dir_name); }
return 0; }

15\. Implement a C program to count the number of lines in a file named
\"data.txt\"?

#include \<stdio.h\> #include \<stdlib.h\> int main() { FILE \*file;
char ch; int line_count = 0; file = fopen(\"data.txt\", \"r\"); if (file
== NULL) { printf(\"Error opening file.\\n\"); return 1; // Return an
error code } while ((ch = fgetc(file)) != EOF) { if (ch == \'\\n\') {
line_count++; // Increment line count if newline character is found } }
fclose(file); printf(\"Number of lines in the file: %d\\n\",
line_count); }

16\. Write a C program to append \"Goodbye!\" to the end of an existing
file named \"message.txt\"?

#include \<stdio.h\> int main() { FILE \*fp; fp = fopen(\"message.txt\",
\"a\"); if (fp == NULL) { printf(\"Error opening file.\\n\"); return 1;
} fprintf(fp, \"Goodbye!\"); fclose(fp); printf(\"Text appended
successfully.\\n\"); return 0; }

17\. Implement a C program to change the permissions of a file named
\"file.txt\" to read only?

#include \<stdio.h\> #include \<sys/stat.h\> #include \<errno.h\> int
main() { const char \*filename = \"file.txt\"; mode_t new_permissions =
S_IRUSR \| S_IRGRP \| S_IROTH; if(chmod(filename, new_permissions) == 0)
{ printf(\"Permissions changed successfully for %s to read-only.\\n\",
filename); } else { perror(\"Error changing permissions\"); return 1; }
return 0; }

18\. Write a C program to change the ownership of a file named
\"file.txt\" to the user \"user1\"?

#include \<stdio.h\> #include \<stdlib.h\> #include \<unistd.h\>
#include \<sys/types.h\> #include \<pwd.h\> int main() { const char
\*filename = \"file.txt\"; const char \*username = \"user1\"; struct
passwd \*pwd = getpwnam(username); if(pwd == NULL) {
perror(\"getpwnam\"); fprintf(stderr, \"Could not find user: %s\\n\",
username); return 1; } uid_t uid = pwd-\>pw_uid; if (chown(filename,
uid, -1) == -1) { perror(\"chown\"); return 1; } printf(\"Ownership of
\'%s\' changed to user \'%s\' (UID: %d)\\n\", filename, username, uid);
return 0; }

19\. Develop a C program to get the last modified timestamp of a file
named \"file.txt\"?

#include \<stdio.h\> #include \<sys/stat.h\> #include \<time.h\> int
main() { struct stat file_stat; const char \*filename = \"file.txt\";
if(stat(filename, &file_stat) == 0) { time_t last_modified_time =
file_stat.st_mtime; printf(\"Last modified time: %ld\\n\",
last_modified_time); struct tm \*time_info; time_info =
localtime(&last_modified_time); char time_string\[100\];
strftime(time_string, sizeof(time_string), \"%Y-%m-%d %H:%M:%S\",
time_info); printf(\"Last modified time (human readable): %s\\n\",
time_string); } else { perror(\"Error getting file stat\"); return 1; }
return 0; }

20\. Implement a C program to create a temporary file and write some
data to it?

#include \<stdio.h\> #include \<stdlib.h\> #include \<string.h\> int
main() { FILE \*tempFile; char \*data = \"Hello, this is some data
written to the temporary file.\\n\"; tempFile = tmpfile(); if(tempFile
== NULL) { perror(\"Error creating temporary file\"); return
EXIT_FAILURE; } if (fputs(data, tempFile) == EOF) { perror(\"Error
writing to the temporary file\"); fclose(tempFile); return EXIT_FAILURE;
} rewind(tempFile); char buffer\[256\]; while (fgets(buffer,
sizeof(buffer), tempFile) != NULL) { printf(\"%s\", buffer); }
fclose(tempFile); printf(\"Temporary file operations completed.\\n\");
return EXIT_SUCCESS; }
