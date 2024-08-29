# wallet_address

0x91B587A4B3Be0371dC0c098Dc0F7c8dEdc4C95Ce


import hashlib

def hashh(text):
    print(str(text))
    d = hashlib.sha256(str(text).encode('utf-8')).hexdigest()
    return d

# Initial data
a = [1, 2, 3, 4, 5, 6, 7, 8]
b = []
d1 = []
i = 0

# Create the first level of hashes
while i < len(a):
    d1.append(hashh(a[i]))
    i += 1

print(d1)
b.append(d1)

# Build the Merkle tree
i = 0
while True:
    k = 0
    c = []
    while k < len(b[i]):
        if k + 1 < len(b[i]):
            combined_hash = hashh(b[i][k] + b[i][k + 1])
            c.append(combined_hash)
        else:
            c.append(b[i][k])
        k += 2

    b.append(c)
    print(i, "b[i]", b[i])

    if len(b[i]) == 1:
        break

    i += 1
