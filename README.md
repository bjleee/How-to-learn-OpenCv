# How-to-learn-OpenCv

## Chapter 1: Read Images Videos and Webcams

- To initialise object and read file 

```ç++
string path = "";
Mat img = imread(path);
```

- Handle base case: empty file

```
if (img.empty()) return -1;
```

