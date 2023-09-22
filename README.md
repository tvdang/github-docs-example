# Writing good documentation

## Step 1 - Using codeblocks . 

codeblocks in markdown make it *very easy* for tech people to **copy, past ,share** their code.
A good cloud engineer uses code blocks where possible.

Allows other to copy and paste their code to replicate or research issues.

```C#
local pm = GetProjectManager();
if (IsNull(pm))
{
    ShowError(_T("Could not query the project manager. Cannot continue."));
    return 0;
}

local p = pm.GetActiveProject();

// File with the source files separated by \n
// for example:
// '''''''''''''''''''
// a.cpp
// b.cpp
// '''''''''''''''''''
local filecontent = IO.ReadFileContents (_T("D:\\ddddd\\fileList.txt"));

// Split the files in lines
local fileList = GetArrayFromString(filecontent, _T("\n"), true);
print(_T("Files to load:"));
for(local i = 0; i < fileList.GetCount(); i++)
{
	print(fileList.Item(i) + _T("\n"));   // Print the files in the list, as a check
}

// Base path, the files in the text files are relative in my case. If they are absolute you can remove this
local basePath = _T("D:\\ddddd\\src\\");
for(local i = 0; i < fileList.GetCount(); i++)
{
        // Create file path
	local filePath = basePath + fileList.Item(i);
	// Add to all build targets
	for(local a = 0; a <= p.GetBuildTargetsCount(); a++)
	    pm.AddFileToProject(filePath, p, a);
}
// Save the project. This triggers also an update of the project UI
pm.SaveAllProjects();
```

![backtick-key](https://www.cnet.com/a/img/resize/69256d2623afcbaa911f08edc45fb2d3f6a8e172/hub/2023/02/03/afedd3ee-671d-4189-bf39-4f312248fb27/gettyimages-1042132904.jpg?auto=webp&fit=crop&height=675&width=1200)

<img width="200px" src = "https://www.cnet.com/a/img/resize/69256d2623afcbaa911f08edc45fb2d3f6a8e172/hub/2023/02/03/afedd3ee-671d-4189-bf39-4f312248fb27/gettyimages-1042132904.jpg?auto=webp&fit=crop&height=675&width=1200"/>
