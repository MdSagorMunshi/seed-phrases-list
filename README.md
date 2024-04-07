## **Project: Seed Phrases List**

This repository contains a large dataset of seed phrases, distributed across three files for a total of approximately 9 million phrases. Due to their size, these files are hosted on Hugging Face. **Please exercise extreme caution when utilizing this data.**

* HuggingFace Dataset: [SEED-PHRASES-LIST](https://huggingface.co/LAYEK-143/seed-phrases-list/tree/master) 

### **IMPORTANT SECURITY CONSIDERATIONS**

* **Seed phrases grant full control over associated cryptocurrency wallets.** Anyone possessing a seed phrase can access and transfer the funds within the wallet.
* **Never share your seed phrases with anyone.**
* **Store seed phrases offline in a secure location.**  Hardware wallets are highly recommended.
* **Treat this dataset with the utmost security.**  Unauthorized access could lead to significant financial loss.

### **About the Dataset**

* **Total Size:** Approximately 9 million seed phrases.
* **Distribution:**
    * File 1: 999,999 seed phrases
    * File 2: 1,000,000 seed phrases
    * File 3: 7,000,000 seed phrases
    * File 4: 10,000,000 seed phrase
    * File 5: 1,000,000 24 words seed phrase (**Coming Down the Pike**)
    * File 4: 10,000,000 24 words seed phrase (**Coming Down the Pike**)
* **Format:** Plain text files (.txt) with the structure: [ACCOUNT <NO>]: SEED PHRASE: (seed phrase here)
* **Source:** Generated using Python code with a focus on BIP39 compatibility for security research. 

**Code**
<details>
  <summary>Show Code</summary>

  ```python
import random
from mnemonic import Mnemonic

def generate_seed_phrase(word_count=12):
    """Generates a BIP39 seed phrase with the specified number of words"""
    
    if word_count not in [12, 24]:
        print("Invalid word count. Defaulting to 12 words.")
        word_count = 12

    mnemo = Mnemonic("english")
    entropy_bits = 128 if word_count == 12 else 256
    entropy = random.getrandbits(entropy_bits) 
    mnemonic = mnemo.to_mnemonic(entropy.to_bytes(entropy_bits // 8, byteorder='big'))
    return mnemonic

def save_seed_phrases(seed_phrases, filename="seed_phrases.txt"):
    """Saves a list of seed phrases to a file"""
    with open(filename, "w") as f:
        for i, seed_phrase in enumerate(seed_phrases):
            f.write(f"[ACCOUNT {i+1}]: SEED PHRASE: {seed_phrase}\n")

def main():
    num_seed_phrases = int(input("How many seed phrases do you want to generate? "))

    seed_phrases = [generate_seed_phrase() for _ in range(num_seed_phrases)]
    save_seed_phrases(seed_phrases) 

    print("Seed phrases generated and saved successfully!")

if __name__ == "__main__":
    main()
  ```
</details>

### **Potential Use Cases**

* **Security Research:** Analyze seed phrase patterns and vulnerabilities.
* **Educational Demonstrations:**  Illustrate the critical importance of seed phrase security. 
* **NOT RECOMMENDED:** Direct use in cryptocurrency wallets. 

### **How to Download**

**Option 1: Hugging Face Hub Interface**

1. Navigate to the file you want to download on the Hugging Face dataset.
2. Click the "Download" button.
3. Choose a download location on your computer.

**Option 2: Cloning the Hugging Face Repository (using Git LFS)**

1. Ensure you have Git Large File Storage (Git LFS) installed: https://git-lfs.github.com/
2. Run the following command in your terminal, replacing the placeholder with the Hugging Face repository link: 
   ```bash
   git clone --branch master --single-branch https://huggingface.co/LAYEK-143/seed-phrases-list.git
   cd seed-phrases-list
   git lfs fetch
   git pull origin master

   ```

### **Disclaimer**

Use of this dataset is entirely at your own risk. The authors and maintainers of this repository assume no responsibility for any losses incurred due to the use or misuse of these seed phrases.

### **FAQ**

* **Q: Why are you providing this dataset?**
    * A: This dataset is intended for security researchers and analysts. By providing access to a large collection of seed phrases, researchers can identify patterns, weaknesses, and potential vulnerabilities commonly exploited by attackers.

* **Q:  Can I use these seed phrases in my own wallet?** 
    * A: Absolutely not! These seed phrases are for research and educational purposes only. Using them in a real wallet poses a serious risk of financial loss.

### **Contact**

* For issues related to the Hugging Face dataset, please open an issue on Hugging Face or contact me directly at **x@thesagor.com**

