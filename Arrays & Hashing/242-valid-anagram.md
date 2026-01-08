# Valid Anagram

## 🧩 Problem

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`,
and `false` otherwise.

An anagram is formed by rearranging the letters of a string using all
the original letters exactly once.

---

## 🧠 Approach

Store the frequency of each character in both strings using dictionaries.
Then, compare the characters and their frequencies to ensure they match.

---

## Solution (C#)
~~~csharp
	public class Solution
	{
		public bool IsAnagram(string s, string t)
		{
			//checking from the first if the 2 strings you are getting have same n of chars or not
			if (s.Length != t.Length)
			{
				return false;
			}

			char[] S_array= s.ToCharArray();

			//dictionary to know each char with its frequencies
			Dictionary<char, int> S_dict= new Dictionary<char, int>(); //empty dict 
			//we need to add the char in the dictionary , but if its alreayd there we will not add it again we just increase value
			for (int i=0; i< S_array.Length;i++)
			{
				//int char_frequencies = 0;
				if (S_dict.ContainsKey(S_array[i]))
				{
					//char_frequencies += 1;
					S_dict[S_array[i]] += 1 ; //old value + 1
				}
				else 
				{
					//if the char is new , so add it into the dicationary as a new key and make its frequency=1
					S_dict.Add(S_array[i], 1);
				}

			}


			char[] T_array = t.ToCharArray();

			Dictionary<char, int> T_dict = new Dictionary<char, int>();

			for (int i = 0; i < T_array.Length; i++)
			{
				if (T_dict.ContainsKey(T_array[i]))
				{

					T_dict[T_array[i]] += 1; //old value + 1
				}
				else
				{
					//if the char is new , so add it into the dicationary as a new key and make its frequency=1
					T_dict.Add(T_array[i], 1);
				}

			}

			//now we have 2 dict , S_dict , and T_dict , each one contains the chars and frequencies of each string
			//now what we need to do is to compare the 2 dict and see if they contain the same chars with same frequencies 
			//if they contain the same chars with same frequencies , return true ,,,,, otherwise return false
			//Problem now: how can we compare the 2 dict with each other

			//Comparing should be
			//1- Compare n of Chars
			//2- check if each char in S_dict is in T_dict
			//3- check if each char have the same frequency in both dicts

			foreach (char i in S_dict.Keys)
			{
				
				if (T_dict.ContainsKey(i) && S_dict[i] == T_dict[i])
				{

				}
				else
				{
					return false;
				}
			}

			return true;


		}
	}
~~~
---
### Complexity
- Time Complexity: O(n)
- Space Complexity: O(n)