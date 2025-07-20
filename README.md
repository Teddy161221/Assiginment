# Assiginment 1
import os

def create_and_write_file(filename, content):
    try:
        # Check if file already exists
        if os.path.exists(filename):
            raise FileExistsError(f"The file '{filename}' already exists.")
        
        # Create and write to the file
        with open(filename, 'w') as file:
            file.write(content)
        print(f"File '{filename}' created successfully with the content.")
    
    except FileExistsError:
        # Pass on file exists error (silently ignore)
        pass
    except Exception as e:
        print(f"An error occurred: {e}")

# File details
file_name = "my_file.txt"
file_content = "this is my file"

# Call the function
create_and_write_file(file_name, file_content)




Assiginment 2

import os
from pathlib import Path

def create_file_on_desktop():
    try:
        # Get the desktop path in a cross-platform way
        desktop_path = Path.home() / "Desktop"
        
        # Alternative desktop path names for different OS/languages
        if not desktop_path.exists():
            desktop_path = Path.home() / "Desktop"
            if not desktop_path.exists():
                desktop_path = Path.home() / "desktop"  # Linux sometimes uses lowercase
        
        # Create the full file path
        file_path = desktop_path / "hello.txt"
        
        # Write content to the file
        with open(file_path, 'w') as file:
            file.write("this is my file")
        
        print(f"File created successfully at: {file_path}")
    
    except Exception as e:
        print(f"Error creating file: {e}")

# Run the function
create_file_on_desktop()


Assiginment 3

def read_file_with_input():
    try:
        # Get file path from user input
        file_path = input("Enter the path of the text file you want to read: ")
        
        # Open and read the file
        with open(file_path, 'r') as file:
            contents = file.read()
        
        # Display file contents
        print("\nFile contents:")
        print("--------------")
        print(contents)
        print("--------------")
        
    except FileNotFoundError:
        print(f"Error: The file '{file_path}' was not found.")
    except PermissionError:
        print(f"Error: You don't have permission to read '{file_path}'.")
    except UnicodeDecodeError:
        print("Error: The file contains non-text data or wrong encoding.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")

# Run the program
if __name__ == "__main__":
    print("File Reader Program")
    print("-------------------")
    read_file_with_input()


    Assiginment 4

    import os

def delete_file_if_exists():
    # Get file path from user input
    file_path = input("Enter the path of the file you want to delete: ")
    
    # Expand ~ to home directory if present
    file_path = os.path.expanduser(file_path)
    
    # Check if file exists
    if os.path.exists(file_path):
        try:
            # Delete the file
            os.remove(file_path)
            print(f"Successfully deleted: {file_path}")
        except PermissionError:
            print(f"Error: Permission denied - cannot delete {file_path}")
        except IsADirectoryError:
            print(f"Error: {file_path} is a directory, not a file")
        except Exception as e:
            print(f"Error occurred while deleting: {e}")
    else:
        print(f"File does not exist: {file_path}")

# Run the program
if __name__ == "__main__":
    print("=== File Deletion Program ===")
    delete_file_if_exists()
