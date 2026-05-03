# 10. Retrieving web content

## 10.1. Retrieving Web content using curl

In the course of many projects, it is necessary to fetch data from an online database or other Internet resource. The standard way to browse to a Web page and then either click to download a linked file, or copy and paste text from the browser window into another document. These methods become impractical when data are spread across multiple pages, or when the data need to be updated from the source on a regular basis. Fortunately, a shell program called `curl` (that is, “see URL”), can directly access Internet files on your behalf, downloading the text content of a Web page without any need of a browser window.

The simplest `curl` command consists of `curl` followed by the Web address (also called a URL) of the item you want to retrieve. In the shell window, type the following command:

```bash
$ cd ../sandbox

$ curl "http://files.rcsb.org/download/1EMA.pdb"
```

When you press `Enter`, the content of that address (a file describing 3-D protein structure) will be downloaded to your terminal so that it scrolls across the screen. If you want to save the information to a file instead, you can use the redirect `>` followed by a file name:

```bash
$ curl "http://files.rcsb.org/download/1EMA.pdb" > 1EMA.pdb
```

To store files without using the redirect operator, use the `-o` option (output) followed by the destination file name. In this case you can say:

```bash
$ curl "http://files.rcsb.org/download/1EMA.pdb" -o 1EMA.pdb
```

The `curl` command really begins to become powerful when you use it to download a range of files in one step. To form this kind of query, put the elements in curly brackets `{ }` separated by commas. For instance, to retrieve a set of four particular protein structures at once, you could use:

```bash
$ curl -O "https://files.rcsb.org/download/{1EMA,1GFL,1G7K,1XMZ}.pdb"
```

By using the `-O` option, the downloaded files are stored under the original file names. You can also specify a range between square brackets, e.g. `[01-31]`.

There are many variations on the queries that you can form with `curl`. Take a look at the `man` page for `curl` for more information on how to tailor your Web downloads.

[Go to exercises in module 11](11-Exercises.md)
