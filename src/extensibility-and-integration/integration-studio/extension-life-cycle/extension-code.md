# Code the Extension

After [defining your extension](<extension-define.md>) in Integration Studio, you have to code the extension and develop it using a .NET IDE. You can specify the IDE to be used in the [Options Window](<../../../ref/integration-studio/menu/edit/options.md>). Learn more on how to [Configure Integration Studio](<https://www.outsystems.com/goto/howto-configure-integration-studio>).

All the [extension elements](<../getting-started/extension.md#extension-elements>) you have defined in Integration Studio are mapped as follows:

Actions
:   Actions are mapped to .NET class methods, in the `<ExtensionName>.cs` file.

Entities and Structures
:    Entities and Structures are mapped to .NET classes and structures, in the `Entities.cs` and `Structures.cs` files.
  
## How to Code an Extension

1. In the .NET IDE, open the solution and code the third-party methods according to your needs. You can use the [Edit Source Code operation](<extension-code-edit.md>).

1. Compile / build the .NET project to generate the main DLL (a .NET assembly) that implements the extension behavior.

When the extension is created, Integration Studio automatically generates the template files needed for the development bootstrap. For more information, see [Extension Source Files](<../getting-started/extension-source-files.md>).

<div class="info" markdown="1">

Template files are the files needed to generate the extension assembly without any custom code, without any code written by the developer. These files are implicitly generated by Integration Studio in the following operations: Create a new Extension, Update the Extension Source Code, or Compare with Template. 

</div>

Typically, these are all the files you need in the development of the extension. However, if more files are necessary, for example a Help file or another DLL, simply add them as dependencies of your third-party project. Afterwards, you should [add them as resources](<../managing-extensions/resource-define.md>) of your extension in order to have all the files packed in the extension.

## Source Change Management

Integration Studio has the necessary mechanisms to synchronize what you do in the tool itself and in the IDE, in order that no information is lost between these two environment tools.

On one hand, some of the changes you have made in the IDE are automatically synchronized in your extension; you don't have to explicit refresh the DLL/JAR or add, as resources, the dependencies of your third-party solution, located in the `Binaries` folder. Simply [verify the extension](<extension-verify.md>) or use the [1-Click Publish operation](<extension-1-cp.md>), and these changes made in the source code are updated in the extension.

<div class="warning" markdown="1">

Changes in the signature of your actions should not be done in the IDE; you should change the action directly in Integration Studio, as explained in the next paragraph.

</div>
On the other hand, any element (action, entity, or structure) created or changed in Integration Studio is automatically available or refreshed in the IDE, after invoking the [Update Source Code](<extension-update-source-code.md>) operation. This operation merges the definition of the actions with the code you implemented in the IDE, without losing your source code. The elements of your extension are identified by its name, which means that if you want to change the name of an action, Integration Studio has no way of relating the old action to the new one. In this situation, you have to manually change the name of the respective method in the source code. To help you with this merging operation, you have the [Compare With Template](<../../../ref/integration-studio/resources-tree.md>) operation.