# EX.-NO-3-IMPLEMENTATION-OF-DIGITAL-SIGNATURE-STANDARD

## AIM:
To write a C program to implement the signature scheme named digital signature
standard (Euclidean Algorithm).

## ALGORITHM:

  STEP-1: Alice and Bob are investigating a forgery case of x and y.
  
  STEP-2: X had document signed by him but he says he did not sign that document digitally.
  
  STEP-3: Alice reads the two prime numbers p and a.
  
  STEP-4: He chooses a random co-primes alpha and beta and the x’s original signature x.
  
  STEP-5: With these values, he applies it to the elliptic curve cryptographic equation to obtain y.
  
  STEP-6: Comparing this ‘y’ with actual y’s document, Alice concludes that y is a forgery.

## PROGRAM:
```
def euclid(m, n):
	
	if n == 0:
		return m
	else:
		r = m % n
		return euclid(n, r)
def exteuclid(a, b):
	
	r1 = a
	r2 = b
	s1 = int(1)
	s2 = int(0)
	t1 = int(0)
	t2 = int(1)
	
	while r2 > 0:
		
		q = r1//r2
		r = r1-q * r2
		r1 = r2
		r2 = r
		s = s1-q * s2
		s1 = s2
		s2 = s
		t = t1-q * t2
		t1 = t2
		t2 = t
		
	if t1 < 0:
		t1 = t1 % a
		
	return (r1, t1)

p = 823
q = 953
n = p * q
Pn = (p-1)*(q-1)

key = []

for i in range(2, Pn):
	
	gcd = euclid(Pn, i)
	
	if gcd == 1:
		key.append(i)

e = int(313)
r, d = exteuclid(Pn, e)
if r == 1:
	d = int(d)
	print("decryption key is: ", d)
	
else:
	print("Multiplicative inverse for\
	the given encryption key does not \
	exist. Choose a different encryption key ")


# Enter the message to be sent
M = 19070

# Signature is created by Alice
S = (M**d) % n

M1 = (S**e) % n

# If M = M1 only then Bob accepts
# the message sent by Alice.

if M == M1:
	print("As M = M1, Accept the message sent by Alice")
else:
	print("As M not equal to M1, Do not accept the message sent by Alice ")
```

## OUTPUT:
![image](https://github.com/AnnBlessy/EX.-NO-3-IMPLEMENTATION-OF-DIGITAL-SIGNATURE-STANDARD/assets/119477835/bd65fb4f-8029-4476-9e01-0a5eadc9d769)

## RESULT:
  Thus the simple Code Optimization techniques had been implemented successfully
