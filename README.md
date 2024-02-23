# Python-Assignment-2
# Problem 1 Code :

reverse_file_content(input_file_path):
    try:
       
        with open(input_file_path, 'r') as file:
            content = file.read()

        reversed_content = content[::-1]
      
        with open(input_file_path, 'w') as file:
            file.write(reversed_content)

        print(f"Content of '{input_file_path}' has been successfully reversed and updated in the file.")
    except FileNotFoundError:
        print(f"Error: File '{input_file_path}' not found.")
    except Exception as e:
        print(f"Error: {e}")

input_file_path = 'file1.txt'
reverse_file_content(input_file_path)

 # Problem 2 Code :



def number_to_text(match):

    num_str = match.group()

    try:

        num = int(num_str)

        # Using a library like inflect can help convert numbers to words

        # Install it using: pip install inflect

        import inflect

        p = inflect.engine()

        return p.number_to_words(num)

    except ValueError:

        # Return the original string if it's not a valid integer

        return num_str



def convert_numbers_to_text(input_file_path, output_file_path):

    try:

        # Read the content of the file

        with open(input_file_path, 'r') as file:

            content = file.read()



        # Use regex to find all numbers in the content

        pattern = r'\b\d+\b'

        content = re.sub(pattern, number_to_text, content)



        # Write the updated content to a new file

        with open(output_file_path, 'w') as file:

            file.write(content)



        print(f"Numbers in '{input_file_path}' have been successfully converted to text and saved in '{output_file_path}'.")

    except FileNotFoundError:

        print(f"Error: File '{input_file_path}' not found.")

    except Exception as e:

        print(f"Error: {e}")



# Example usage: replace 'file2.txt' and 'output_file.txt' with the actual file paths

input_file_path = 'file2.txt'

output_file_path = 'output_file.txt'

convert_numbers_to_text(input_file_path, output_file_path)
