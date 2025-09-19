# CS-helper
a computer science bot that helps for year 8 or grade 7 with computer science includes things like vector graphic to microbit
import difflib

    
import difflib


qa_db = {
    "what is a vector graphic": "A vector graphic is an image created using paths defined by mathematical equations, allowing for infinite scalability without loss of quality.",
    "what is a bitmap image": "A bitmap image is composed of a grid of individual pixels, each with its own color, forming a complete image.",
    "what is the difference between vector and bitmap images": "Vector images are resolution-independent and can be scaled without loss of quality, while bitmap images can lose quality when resized due to pixelation.",
    "what is color depth in digital images": "Color depth refers to the number of bits used to represent the color of a single pixel, determining the range of colors an image can display.",
    "what is binary code": "Binary code is a system of representing text or computer processor instructions using the binary number system, which employs only two binary digits: 0 and 1.",
    "what is a cpu": "The Central Processing Unit (CPU) is the primary component of a computer that performs most of the processing inside a computer.",
    "what is ram": "Random Access Memory (RAM) is a type of computer memory that can be accessed randomly, allowing data to be read or written in nearly the same amount of time.",
    "what is a hard drive": "A hard drive is a data storage device used for storing and retrieving digital information using rapidly rotating disks coated with magnetic material.",
    "what is an operating system": "An operating system is system software that manages hardware and software resources and provides common services for computer programs.",
    "what is a computer network": "A computer network is a set of computers connected together for sharing data and resources.",
    "what is the internet": "The internet is a global system of interconnected computer networks that use the Internet Protocol Suite (TCP/IP) to link devices worldwide.",
    "what is html": "HyperText Markup Language (HTML) is the standard markup language used to create web pages.",
    "what is css": "Cascading Style Sheets (CSS) is a style sheet language used for describing the presentation of a document written in HTML or XML.",
    "what is javascript": "JavaScript is a programming language commonly used to create interactive effects within web browsers.",
    "what is a website": "A website is a collection of related web pages, images, videos, or other digital assets that are addresmsed relative to a common Uniform Resource Locator (URL).",
    "what is a webpage": "A webpage is a document commonly written in HTML that is accessible through the internet.",
    "what is a hyperlink": "A hyperlink is a reference to data that the user can follow by clicking or tapping.",
    "what is a domain name": "A domain name is an identification string that defines a realm of administrative autonomy, authority, or control within the Internet.",
    "what is a web browser": "A web browser is a software application for accessing information on the World Wide Web.",
    "what is a search engine": "A search engine is a software system designed to carry out web searches, allowing users to find information on the World Wide Web.",
    "what is a database": "A database is an organized collection of data, generally stored and accessed electronically from a computer system.",
    "what is a server": "A server is a computer program or device that provides functionality for other programs or devices, called clients.",
    "what is cloud computing": "Cloud computing is the delivery of computing services over the internet, including storage, processing, and software.",
    "what is an algorithm": "An algorithm is a set of step-by-step instructions for solving a problem or performing a task.",
    "what is a flowchart": "A flowchart is a diagram that represents a process or workflow, showing steps and decision points.",
    "what is a loop": "A loop is a programming structure that repeats a set of instructions until a certain condition is met.",
    "what is a variable": "A variable is a storage location in programming with a name that holds data which can be changed during program execution.",
    "what is a constant": "A constant is a value in programming that cannot be changed during program execution.",
    "what is a function": "A function is a reusable block of code that performs a specific task.",
    "what is an array": "An array is a collection of elements, typically of the same type, stored in contiguous memory locations.",
    "what is a list": "A list is a collection of ordered elements that can contain multiple data types.",
    "what is a string": "A string is a sequence of characters used to represent text in programming.",
    "what is an integer": "An integer is a whole number, positive or negative, without any decimal point.",
    "what is a float": "A float is a number that has a decimal point.",
    "what is a boolean": "A boolean is a data type with only two possible values: True or False.",
    "what is a conditional statement": "A conditional statement allows a program to execute certain code only if a specified condition is true.",
    "what is an if statement": "An if statement executes a block of code if a specified condition evaluates to True.",
    "what is an else statement": "An else statement executes a block of code if the preceding if condition is False.",
    "what is an elseif statement": "An elseif (or elif) statement checks another condition if the previous if statement is False.",
    "what is a for loop": "A for loop repeats a block of code a specific number of times.",
    "what is a while loop": "A while loop repeats a block of code as long as a condition is True.",
    "what is a nested loop": "A nested loop is a loop inside another loop.",
    "what is an operator": "An operator is a symbol that performs operations on variables and values.",
    "what is an arithmetic operator": "Arithmetic operators perform mathematical operations like addition, subtraction, multiplication, and division.",
    "what is a comparison operator": "Comparison operators compare two values and return a boolean result.",
    "what is a logical operator": "Logical operators combine boolean expressions, such as AND, OR, and NOT.",
    "what is debugging": "Debugging is the process of identifying and fixing errors in a program.",
    "what is pseudocode": "Pseudocode is a plain language description of the steps in an algorithm, not bound to a programming language.",
    "what is data representation": "Data representation is how information is encoded for storage or processing in a computer.",
    "what is binary": "Binary is a number system using only 0s and 1s, used internally by almost all computers and digital systems.",
    "what is hexadecimal": "Hexadecimal is a base-16 number system used in computing as a human-friendly representation of binary-coded values.",
    "what is ascii": "ASCII is a character encoding standard for electronic communication, representing text in computers.",
    "what is unicode": "Unicode is a universal character encoding standard that includes characters from almost all written languages.",
    "what is input": "Input is data sent to a computer for processing.",
    "what is output": "Output is data produced by a computer after processing.",
    "what is storage": "Storage is the component of a computer that holds data, either temporarily or permanently.",
    "what is secondary storage": "Secondary storage refers to devices like hard drives and SSDs that store data permanently.",
    "what is primary storage": "Primary storage refers to memory like RAM that temporarily holds data for active processes.",
    "what is cybersecurity": "Cybersecurity is the practice of protecting systems, networks, and programs from digital attacks.",
    "what is malware": "Malware is malicious software designed to harm or exploit computers and networks.",
    "what is a virus": "A virus is a type of malware that attaches itself to files and spreads between computers.",
    "what is a firewall": "A firewall is a network security device or software that monitors and controls incoming and outgoing network traffic.",
    "what is encryption": "Encryption is the process of converting information into a code to prevent unauthorized access.",
    "what is decryption": "Decryption is the process of converting encrypted data back into its original form.",
    "what is ethical hacking": "Ethical hacking is the practice of legally probing systems to find security vulnerabilities.",
    "what is a backup": "A backup is a copy of data stored separately to prevent data loss.",
    "what is cloud storage": "Cloud storage is storing data on remote servers accessed via the internet.",
    "what is machine learning": "artificial intelligence that uses algorithms trained on data sets to create models capable of performing tasks.",



}

def search_answer(query):
    query_lower = query.lower()
    # Exact match
    if query_lower in qa_db:
        return qa_db[query_lower]
    # Fuzzy match
    matches = difflib.get_close_matches(query_lower, qa_db.keys(), n=1, cutoff=0.6)
    if matches:
        return qa_db[matches[0]]
    return "Sorry, I don't know the answer yet."

def help_menu():
    print("Commands:")
    print("  ask <question>    - Ask a question")
    print("  help              - Show this menu")
    print("  exit              - Quit")

def repl():
    print("Computer science (type 'help' for commands)")
    while True:
        try:
            command = input("> ").strip()
        except (EOFError, KeyboardInterrupt):
            print("\nExiting.")
            break
        if not command:
            continue
        if command.lower() == "help":
            help_menu()
        elif command.lower() == "exit":
            break
        elif command.lower().startswith("ask "):
            question = command[4:]
            answer = search_answer(question)
            print("Answer:", answer)
        else:
            print("Unknown command. Type 'help' for options.")

if __name__ == "__main__":
    repl()
