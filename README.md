# Checklist:

## 1. Create a new Class Library project in Visual Studio
  - Open Visual Studio
  - Click on "Create a new project"
  - Choose "Class Library (.NET Framework)"
  - Name the project and set the location
  - Click "Create"

## 2. Build Configuration
  - Click on the "Project" tab > "<ProjectName> Properties"
  - Click on the "Build" tab and select "x64" from the "Platform Target" drop-down
  - Click on the "Debug" tab and activate the "Start External Program" radio button
  - Browse to your Revit root folder and locate/select the "Revit.exe" file
  - `C:\Program Files\Autodesk\Revit <year>`
  - [Click on "Tools" > "Options" > "Debugging" > "General" and ensure "Use Managed Compatibility Mode" is checked](https://forum.dynamobim.com/t/setting-up-the-c-environment/76350?u=turtlewolfe "yeah, I was just trying to follow the directions. So, it’s safe to skip this one?")
  - Click on "Tools" > "Options" > "Projects and Solutions" > "Build and Run" and ensure "Always build" option is selected under "On Run, when projects are out of date"

## 3. Configure .csproj File
  - Right-click on the solution file in the Solution Explorer and click "Unload Project"
  - Right-click the solution file in the Solution Explorer again and click "Edit <ProjectName>.csproj"
  - Scroll down to the bottom of the file and copy and paste the provided XML snippet before the closing </project> tag
  - Save the changes and right-click on the project in the Solution Explorer, then select "Reload Project"

## 4. Create Custom Package JSON
  - Create a new text file (txt) and copy the provided JSON code into the file
  - Rename the file extension to .json (ignore any Windows warning about changing file extensions)
  - Add the JSON file to the Visual Studio project by right-clicking on the solution file in the Solution Explorer and clicking "Add" > "Existing Item", then selecting and opening the JSON file

## 5. Add Dynamo Core, Dynamo Visual Programming, and Revit API references
  - Right-click on "References" in the Solution Explorer
  - Click on "Add Reference"
  - Browse to the location of the required DLL files and add them:
    - Dynamo Core (DynamoCore.dll)
    - Dynamo Visual Programming (DynamoServices.dll)
    - Revit API (RevitAPI.dll and RevitAPIUI.dll)

## 6. Create custom namespace and classes for your nodes (HelloWorld and RevitWall)
  - In the Solution Explorer, right-click on the project and choose "Add" > "Class"
  - Name the class (e.g., HelloWorld.cs and RevitWall.cs) and click "Add"
  - Replace the default namespace and class declarations with your custom namespace and class names

## 7. Add constructors, fields, properties, and methods to the classes
  - In the HelloWorld class, add a private field, a public property, a default constructor, a parameterized constructor, and a method
  - In the RevitWall class, add a private constructor and a public static method

## 8. Utilize TransactionManager and wrap Revit elements using ToDSType() method
  - Add the required using directives to access TransactionManager, DocumentManager, and Revit.Elements
  - In the RevitWall class method, create a transaction using TransactionManager.Instance.EnsureInTransaction() and TransactionManager.Instance.TransactionTaskDone()
  - Wrap the Revit wall element using the ToDSType() method before returning it

## 9. Set the output path for the build
  - In Visual Studio, right-click on the project in the Solution Explorer and select "Properties"
  - Click on the "Build" tab
  - Set the "Output path" to the Dynamo packages folder (usually located at C:\Users\<username>\AppData\Roaming\Dynamo\Dynamo Revit\<version>\packages)

## 10. Compile the solution and create a DLL file
  - In Visual Studio, click on "Build" > "Build Solution"
  - The DLL file will be generated in the specified output path (Dynamo packages folder)

## 11. Test the custom nodes in Dynamo
  - Open Revit and create a new project or open an existing one
  - Go to the "Manage" tab and click on "Dynamo" to launch the Dynamo workspace
  - In the Dynamo workspace, click on "Library" on the left side to view the available nodes
  - Find your custom nodes (HelloWorld and RevitWall) under the custom namespace you created (e.g., ZeroTouchNodes)
  - Drag and drop the custom nodes onto the workspace
  - Connect the required inputs to the nodes and run the Dynamo script to test their functionality
  - Verify that the custom nodes are working as intended
