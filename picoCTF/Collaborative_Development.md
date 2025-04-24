# Collaborative Development
Write-Up by **Mttttt** *2024-05-29*

## Task description
.

- *Category*: **General Skills**
- *Difficulty*: **Easy**

## Solution
See all branches
```bash
git branch -a
```

Got these branches:
- feature/part-1
- feature/part-2
- feature/part-3

Change current branch
```bash
git checkout feature/part-1
```

See content of `flag.py`
```python3
print("Printing the flag...")  
print("picoCTF{t3@mw0rk_", end='')
```

On `feature/part-2`:
```python3
print("Printing the flag...") 
print("m@k3s_th3_dr3@m_", end='')
```

On `feature/part-3`:
```python3
print("Printing the flag...")
print("w0rk_798f9981}")
```

Result:
`picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}`

## Answer
`picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}`
