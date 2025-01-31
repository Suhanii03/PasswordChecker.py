# PasswordChecker.py 
 
  
   
    import re

 
  
   
    def check_password_strength(password):
     
     score = 0
     
     feedback = ""

    if len(password) >= 8:
        score += 20
    else:
        feedback += "Password too short. Minimum length is 8 characters.\n"

    if re.search(r"[A-Z]", password):
        score += 15
    else:
        feedback += "Password must contain uppercase letters.\n"

    if re.search(r"[a-z]", password):
        score += 15
    else:
        feedback += "Password must contain lowercase letters.\n"

    if re.search(r"[0-9]", password):
        score += 15
    else:
        feedback += "Password must contain digits.\n"

    if re.search(r"[!@#$%^&*]", password):
        score += 15
    else:
        feedback += "Password must contain special characters (!@#$%^&*).\n"

    # (Optional) Check against common passwords (requires a list or API)
    # For this example, we'll skip it to keep the code concise

    if not re.search(r"(.)\1{2,}", password): # Check for repeated characters (3 or more)
      score += 10
    else:
      feedback += "Avoid repeating characters.\n"

    if not re.search(r"abc|bcd|cde|def|efg|fgh|ghi|hij|ijk|jkl|klm|lmn|mno|nop|opq|pqr|qrs|rst|stu|tuv|uvw|vwx|wxy|xyz", password.lower()):
      score += 10
    else:
      feedback += "Avoid sequential characters (e.g., abc, 123).\n"

    strength_rating = calculate_rating(score)

    return strength_rating, feedback 
    def calculate_rating(score):
    if score < 50:
        return "Weak"
    elif score < 80:
        return "Medium"
    else:
        return "Strong"b
        while True:
    password = input("Enter password (or type 'exit'): ")
    if password.lower() == "exit":
        break

    rating, feedback = check_password_strength(password)
    print(f"Strength: {rating}")
    if feedback:
        print("Feedback:")
        print(feedback)
    print("-" * 20)  
    
Enter Password : 12345 

Strength: Weak 

Feedback:
Password too short. Minimum length is 8 characters. 

Password must contain uppercase letters. 

Password must contain lowercase letters. 

Password must contain special characters (!@#$%^&*).  

Enter password (or type 'exit'): 1234abcd 

Strength: Medium 

Feedback:
Password must contain uppercase letters. 

Password must contain special characters (!@#$%^&*). 

Avoid sequential characters (e.g., abc, 123).

 
