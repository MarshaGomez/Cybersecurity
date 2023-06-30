# Cybersecurity. Exam Practice 
Course Foundations of Cybersecurity with Professor Dini

## Theory

### Exercise n.1

State and prove the Shannon’s Theorem.

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.2

Explain the RSA key generation algorithm, discussing the complexity of each step.

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.3

Describe the meet-in-the-middle attack to 2DES and argue about its complexity.

<details><summary>Solution</summary>
<p>
  
</p>
</details>


### Exercise n.4

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.5

1. Illustrate the authenticated encryption (AE) scheme *encrypt and authenticate*.
2. Argue whether it can be considered secure.
3. Illustrate the AE scheme “encrypt then authenticate”.

<details><summary>Solution</summary>
<p>
  
</p>
</details>


## Analysis

### Exercise n.1

The hash function H(·) suffers from collision attacks in $2^{41}$, exploiting the inner structure function and simply appending properly crafted blocks to the message. Besides this, the size of H(·), 128 bits, limits its maximum collision resistance to $2^{64}$.

Willing to strengthen the H(·), three proposals are made:
* a) H-A(m) is defined as SHA2-256(H(m))
* b) H-B(m) is defined as H(SHA2-256(m))
* c) H-C(m) is defined as AESk(H(m)), with a fixed key k
* d) H-D(m) is defined as SHA2-256(H(SHA2−256(m)))


Comment on the improvements to the collision resistance of the resulting hash function. 

<details><summary>Solution</summary>
<p>

Let's analyze each proposal and comment on the improvements to the collision resistance of the resulting hash function:

**a) H-A(m) is defined as SHA2-256(H(m)):**
In this proposal, the hash function H(m) is applied first, followed by SHA2-256. Since SHA2-256 is a widely-used and well-analyzed hash function, it is believed to have a strong collision resistance property. By applying SHA2-256 to the output of H(m), it adds an extra layer of security against collision attacks on the inner structure of H(·). This additional step strengthens the collision resistance of the resulting hash function.

**b) H-B(m) is defined as H(SHA2-256(m)):**
Here, the order of applying the hash functions is reversed compared to the proposal (a). SHA2-256 is applied to the message m first, and then the result is passed through the hash function H(·). Since the inner structure of H(·) was vulnerable to collision attacks, applying SHA2-256 to the message before using H(·) can provide some resistance against these attacks. However, the overall improvement in collision resistance may not be as strong as in proposal (a) because the vulnerable inner structure of H(·) is still present.

**c) H-C(m) is defined as AESk(H(m)), with a fixed key k:**
In this proposal, the output of H(m) is encrypted using the AES (Advanced Encryption Standard) algorithm with a fixed key k. AES is a symmetric encryption algorithm widely used and considered secure. By applying AES encryption to the output of H(m), introduces an additional layer of complexity and makes it harder for an attacker to find collisions. However, it's important to note that the collision resistance of this proposal relies on the security of AES and the secrecy of the fixed key k.

**d) H-D(m) is defined as SHA2-256(H(SHA2−256(m))):**
This proposal combines the ideas from both proposal (a) and proposal (b). The message m is first passed through SHA2-256, then H(·) is applied, and finally, the resulting hash is passed through SHA2-256 again. By applying SHA2-256 twice, it adds an additional layer of security against collision attacks on the inner structure of H(·). This approach is similar to the proposal (a) but with an extra step of applying SHA2-256 to the final hash. As a result, it further strengthens the collision resistance compared to the original H(·) hash function.

In summary, among the given proposals, (a) and (d) offer the most significant improvements to the collision resistance of the resulting hash function. Proposal (a) applies SHA2-256 to the output of H(m), while proposal (d) applies SHA2-256 twice to the final hash. Both of these approaches add extra layers of security and are likely to enhance collision resistance. Proposal (b) provides some improvement but may not be as strong as (a) and (d) due to the vulnerable inner structure of H(·). Proposal (c) relies on AES encryption, which can provide additional complexity but its collision resistance depends on the security of AES and the secrecy of the fixed key.

</p>
</details>

### Exercise n.2

Alice wishes to protect passwords from an attacker who manages to grab the password file and then perform an offline attack, possibly based on a rainbow table attack. For this reason, Alices decides to salt the hashing. Let p denote a plaintext password and s a 128-bit random salt. 

Alice adopts the following salting scheme: **Scheme 1:** Compute $h = MD5^{1000}(p) ⊕ s$, and store the pair (h, s) in the password file.
* A. Discuss the security of this scheme w.r.t. a rainbow table attack.

Bob suggests Alice employ the following salting scheme: **Scheme 2:** Compute $h = MD5^{1000}(p || s)$, and store (h, s) in the password file.
* B. Is this choice better or worse than Alice’s w.r.t. a rainbow table attack?

Within Scheme 2, assume that users employ 8 characters chosen over the English lowercase alphanumeric characters.
* C. How many bits long should be the salt to prevent an attacker able to compute $2^{70}$ passwords from employing a rainbow table attack?
* D. Does the previous amount of random salt prevent an attacker from brute forcing a single password?

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.3

A client C and server S share a password P. Furthermore, C knows the public key s of the server S. Client’s and server’s clocks are not synchronized. Design a protocol that makes it possible to establish a symmetric session key kcs between the client and the server. The protocol must avoid both the replay attack and the offline password-guessing attack. Furthermore, it must satisfy the key authentication and key confirmation properties.

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.4

Let m be a 256-bit message and mi denote the i-th. Consider the following one-time digital signature scheme.
* Key generation algorithm.
  1. Generate two random sequences $S^0$ and $S^1$, both of 256 elements, defined as follows: $𝑆^𝑘 = {𝑆_{𝑖}^𝑘 , 1 ≤ 𝑖 ≤ 256}, 0 ≤ 𝑘 ≤ 1, s.t., 𝑆_{𝑖}^𝑘 ← random()|_{256}$. Let $S = {S^0, S^1}$ be the private key.
  2. Generate two sequences $P^0$ and $P^1$, defined as follows $𝑃^𝑘 = {𝑃_{𝑖}^𝑘 , 1 ≤ 𝑖 ≤ 256}, 0 ≤ 𝑘 ≤ 1, s.t., 𝑃𝑖𝑘 ← 𝐻(𝑆_{𝑖}^𝑘)$, where H() is a 256-bit one-way hash function. Let $P = {P^0, P^1}$ be the public key.

* Signature generation algorithm. The digital signature $D$ of $m$ is defined as follows:

$$
\forall 1 \leq  i \leq  256, D{i} = 
\begin{Bmatrix}
 S_{i}^0 & \text{if } m_{i} = 0 \\
 S_{i}^1 & \text{if } m_{i} = 1 
\end{Bmatrix}
$$

Answer the following questions.
1. Determine the size in a bit of the digital signature.
2. Specify the signature verification algorithm.
3. Argue about the unforgeability of the signature scheme.
4. Assume the secret key is used to digitally sign two different messages x and y. Let X and Y be their respective digital signatures. Describe a possible existential forgery attack that generates a valid pair (z, Z).

<details><summary>Solution</summary>
<p>
  
</p>
</details>

### Exercise n.5
Assume a threat model in which an adversary can steal the password file and perform an off-line Rainbow Table attack.
* Assume we adopt the following salted hashing technique: $h = H^{1000}(p) ⊕ s$ where $p$ is the plaintext password, $s$ is a 128-bit random salt, and $H$ is a secure one-way has function. The pair $(h, s)$ is stored in the password file on disk. Is this approach secure? Explain why.
* Assume now we adopt the following salted hashing technique: $h = H(p||s)$ and again, we store the pair $(h, s)$ in the password file on disk. Is this choice better than the previous one? Explain why.
* With reference to the second hashing scheme, if users employ 8 characters passwords chosen over the lowercase alphanumeric characters, how many bits long should be the salt to prevent an attacker able to (pre-)compute 270 passwords from employing a Rainbow Table attack?
* Does the previous amount of random salt prevent an attacker from brute-forcing a single password?


<details><summary>Solution</summary>
<p>
  
</p>
</details>

## Secure Coding

### Exercise n.1

Find and explain the vulnerabilities of the following function. Then patch them.
````c++
void ExpandVector(std::vector<int>& c) {
  // This code wants to expand the vector c by doubling each of its
  // elements. For example, the vector [1,2,3] must become
  // [1,1,2,2,3,3].
  auto i = c.begin();
  while (i != c.end()) {
    c.insert(i, *i);
    i++;
  }
}
````

<details><summary>Solution</summary>
<p>

The given function, ExpandVector, intends to double each element in a vector by inserting a copy of each element before the original element. However, it suffers from two vulnerabilities: an infinite loop and an iterator invalidation issue. Let's discuss these vulnerabilities and propose patches for each:

**Infinite Loop:**
The function uses an iterator, 'i,' to traverse the vector and double each element. However, it fails to update the iterator 'i' after inserting the copy of the element. As a result, the iterator remains pointing to the original element, causing an infinite loop where the same element is repeatedly inserted before itself.
Patch for the Infinite Loop vulnerability:
To fix this issue, the iterator 'i' should be updated to point to the next position after inserting the copy of the element. This can be achieved by using the return value of the insert function, which provides an iterator pointing to the newly inserted element. Here's the modified code:

````c++
void ExpandVector(std::vector<int>& c) {
  auto i = c.begin();
  while (i != c.end()) {
    i = c.insert(i, *i);
    i += 2;
  }
}
````

By incrementing **i** by 2 after inserting the copy of the element, we ensure that the iterator moves to the correct position for the next iteration.

**Iterator Invalidation:**
The insert operation in the original code may invalidate the iterator 'i,' leading to undefined behavior. When an element is inserted before the current position, all existing iterators may become invalid. In our case, the iterator 'i' can be invalidated after each insert operation.
Patch for the Iterator Invalidation vulnerability:
To handle iterator invalidation, we can modify the code to use the result of the insert operation as the new iterator for the next iteration. This ensures that the iterator remains valid throughout the loop. Here's the modified code:

````c++
void ExpandVector(std::vector<int>& c) {
  auto i = c.begin();
  while (i != c.end()) {
    i = c.insert(i, *i);
    std::advance(i, 2);
  }
}
````
By using **std::advance(i, 2)** instead of **i += 2**, we guarantee that **i** moves to the correct position while handling any potential iterator invalidation caused by the insert operation.
With these patches, the ExpandVector function should now correctly expand the vector by doubling each of its elements without suffering from an infinite loop or iterator invalidation issues.

  
</p>
</details>

### Exercise n.2

Find and explain the vulnerabilities of the following function. Then patch them.

````c++
void do_stuff(int aux) {
  if (aux<0) {
  /*Handle error*/}
  unsigned char* buf = (char*) malloc(aux);
  if (gets(buf) == NULL) {
    /* Handle error */}
    /* do other stuff */
}
````

<details><summary>Solution</summary>
<p>
  
</p>
</details>


### Exercise n.3

Find and explain the vulnerabilities of function EditStudent, then patch them.

````c++
struct student{
  int StudentID;
  char FirstName[100];
  char LastName[100];
  int DegreeID;
}
void EditStudent(student* stu, int Sid, int Did, char* Fname, char* Lname) {
  //The function replaces the value in the field of the structure pointed to by
  // stu with the values Sid, Did, Fname, Lname
  stu->StudentID = Sid;
  strcpy(stu->FirstName, Fname);
  strcpy(stu->LastName, Lname);
  stu->DegreeID = Did;
}
````

<details><summary>Solution</summary>
<p>

### Exercise n.4

Find and explain the vulnerabilities of the following function. Then patch them.

````c++
void ExpandVector(std::vector<int>& c) {
  //This code expands vector c by doubling each element.
  //For example, vector [1,2,3] becomes [1,1,2,2,3,3].
  for(auto i = c.begin(); i != c.end(); i++) {
    c.insert(i, *i);
  }
}
````

<details><summary>Solution</summary>
<p>
  
</p>
</details>
  
</p>
</details>


### Exercise n.5

<details><summary>Solution</summary>
<p>
  
</p>
</details>

