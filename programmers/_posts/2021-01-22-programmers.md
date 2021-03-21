---
layout: post
title: 스택
---
# 스택

- 고준희
    - 완주하지 못한 선수

        ```python
        def solution(participant, completion):
            participant.sort()
            completion.sort()
            answer = ''
            for i in range(len(completion)):
                if participant[i] == completion[i] :
                    if i==len(completion)-1:
                        answer = participant[-1]
                    continue
                else :
                    answer = participant[i]
                    break
            return answer
        ```

        ```python
        def solution(participant, completion):
            answer = ''
            temp = 0
            dic = {}
            for part in participant:
                dic[hash(part)] = part
                temp += int(hash(part))
            for com in completion:
                temp -= hash(com)
            answer = dic[temp]

            return answer
        ```

        ```python
        from collections import Counter
        def solution(participant, completion):
            par_dic = Counter(participant)
            com_dic = Counter(completion)
            for key, value in par_dic.items():
                if value != com_dic[key]:
                    return key
        ```

    - 전화번호 목록

        ```python
        def solution(phone_book):
            answer = True
            phone_book.sort()
            for i in range(len(phone_book)):
                j=i+1
                if answer == False :
                    break
                while j < len(phone_book):
                    if phone_book[i] == phone_book[j][0:len(phone_book[i])]:
                        answer = False
                        break
                    else :
                        j += 1
            
            return answer
        ```

    - 위장

        ```python
        def solution(clothes):

            clothes_dic={}
            
            for name, kind in clothes:
                if kind in clothes_dic:
                    clothes_dic[kind] += 1
                else:
                    clothes_dic[kind] = 1
            
            answer = 1
            
            for i in clothes_dic.values():
                answer = answer*(i+1)
            
            answer = answer-1
            return answer
        ```
---
- 이현복
    - 완주하지 못한 선수

        수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

        마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

        ```python
        from collections import Counter

        def solution(participant, completion):
            participant_counter = Counter(participant)
            completion_counter = Counter(completion)
            gap = participant_counter - completion_counter
            answer = list(gap)[0]def solution(phone_book):
            answer = True
            phone_book.sort()
            for i in range(len(phone_book)):
                j=i+1
                if answer == False :
                    break
                while j < len(phone_book):
                    if phone_book[i] == phone_book[j][0:len(phone_book[i])]:
                        answer = False
                        break
                    else :
                        j += 1
            
            return answer
            return answer
        ```

        hash function

        Counter 함수

        dictionary의 합차에 대한 이해가 필요함

    - 전화번호 목록

        전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.

        - 구조대 : 119
        - 박준영 : 97 674 223
        - 지영석 : 11 9552 4421

        전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.

        ```python
        def solution(phone_book):
            phone_book.sort()
            for p1, p2 in zip(phone_book, phone_book[1:]):
                if p2.startswith(p1):
                    return False
                else:
                    return True

        ```

        hash function 

        for 문을 통한 in, zip 개념

    - 위장

        스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

        예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.

        스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

        ```python
        def solution(clothes):
            from collections import Counter
            from functools import reduce
            dict = Counter([kind for name, kind in clothes])
            answer = reduce(lambda x, y:x*(y+1), dict.values(), 1)-1
            return answer

        ```

        hash function 을 이해하기 위해선 다음을 알아야 한다

        counter 와 for, in 문을 사용한 dictionary counting 

        reduce, lambda 의 작동 형식

        답을 이끌어내는 함수의 형태
---
- 정효인
    - 주식가격(100)

        ```cpp
        #include <string>
        #include <vector>

        using namespace std;

        vector<int> solution(vector<int> prices) {
            vector<int> answer;
            for(int i=0;i<prices.size()-1;i++)
            {
                for(int j=i+1;j<prices.size();j++)
                {
                    if((prices[i]>prices[j])||(j==(prices.size()-1)))
                    {
                        answer.push_back(j-i);
                        break;
                    }
                }
            }
            answer.push_back(0);
            return answer;
        }
        ```

--- 
- 김건호
    - 완주하지 못한 선수

        ```python
        def solution(participant, completion):
            completion_dic = {}

            for name in completion:
                if name not in completion_dic:
                    completion_dic[name] = 0

                completion_dic[name] += 1
                
            for p_name in participant:
                if p_name not in completion_dic or completion_dic[p_name] == 0:
                    return p_name

                completion_dic[p_name] -= 1
        ```

        ```python
        from collections import Counter

        def solution3(self, participant, completion):
                return list(Counter(participant) - Counter(completion))[0]

        ```

    - 전화번호 목록
        - 이중 포문

            ```python
            # def for_(phone_book: List[str]) -> bool:
            #        for index, phone_number in enumerate(phone_book):
            #            for other_index, other_num in enumerate(phone_book):
            #                if phone_number == other_num[:len(phone_number)] and index != other_index:
            #                    return False
                    
            #        return True

            def prac(phoneBook: List[str]) -> bool:
                    
                    for i in range(len(phoneBook)):
                        for j in range(len(phoneBook)):
                            if phoneBook[i] == phoneBook[j][:len(phoneBook[i])] and i != j:
                                return False

                    return True
            ```

        - 해쉬 (다른 사람의 풀이)

            ```python
            def hash(phone_book: List[str]) -> bool:
                    hash_table = {}
                    
                    for phone_num in phone_book:
                        hash_table[phone_num] = 1
                    
                    for phone_num in phone_book:
                        temp = ""

                        for num in phone_num:
                            temp += num

                            if temp in hash_table and temp != phone_num:
                                return False
                    
                    return True
            ```

            번호를 하나씩 불러와서 그 번호를 prefix로 하는 다른 번호가 있는지 확인하는 것이 아닌,

            번호를 하나 불러오고 그 번호안에 다른 prefix 번호가 있는지 확인하는 방식

    - 위장

        ```python
        import collections

        def solution(clothes):
            hash_table = collections.defaultdict(int)
            cnt = 1
            
            for cloth in clothes:
                hash_table[cloth[1]] += 1
                
            for cloth in hash_table.items():
                cnt *= cloth[1] + 1
                
            return cnt - 1
        ```
---
- 김윤재
    - 완주하지 못한 선수

        ```cpp
        #include <string>
        #include <vector>
        #include <string>
        #include <algorithm>

        using namespace std;

        string solution(vector<string> participant, vector<string> completion) {
            sort(participant.begin(), participant.end());
            sort(completion.begin(), completion.end());
            for(int i=0; i<participant.size(); i++) {
                if(participant[i] != completion[i])
                    return participant[i];
            }
            return "";
        }

        if(participant[i] != completion[i])
        if(participant[i].compare(completion[i]) != 0) // segmentation fault
        ```

    - 전화번호 목록

        ```cpp
        #include <iostream>
        #include <string>
        #include <vector>

        using namespace std;

        int is_prefix(vector<string>& phone_book) {
            vector<vector<string> > HashTable(10);
        		vector<int> count(10, 0), check(10, 0);
            int first_val;
            for(int i=0; i<phone_book.size(); i++) {
                first_val = phone_book[i][0] - 48; // "1"
        				phone_book[i].erase(0,1); //""
        				HashTable[first_val].push_back(phone_book[i]); [1] : ""
                if(phone_book[i].size() == 0) check[first_val] = 1;
        				count[first_val]++;
            }
            
        	for(int i=0; i<10; i++) {
        		if(count[i]>1) {
                    if(check[i] == 1) **return 1;**
                    else {
        			    int result = is_prefix(HashTable[i]);
        			    if(result == 1) **return 1;**
        		    }
        	    }
            }    
            **return 0;**
        }

        bool solution(vector<string> phone_book) {
          bool answer = true;
        	int result = is_prefix(phone_book);
        	if(result == 1) answer = false;
            return answer;
        }
        ```

    - 위장

        ```cpp
        #include <iostream>
        #include <string>
        #include <vector>
        #include <algorithm>

        using namespace std;

        int clothes_MAX = 30;

        bool compare(vector<string>& a, vector<string>& b) {
        	return a[1] < b[1];
        }

        int solution(vector<vector<string>> clothes) {
          int answer = 1;
        	sort(clothes.begin(), clothes.end(), compare);

        	vector<int> count; int temp = 1;
            for(int i=0; i<clothes.size()-1; i++) {
        		if(clothes[i][1] == clothes[i+1][1])
        			temp++;
        		else {
        			count.push_back(temp);
        			temp = 1;
        		}
        	}
        	count.push_back(temp);
        	
        	
        	for(int i=0; i<count.size(); i++) {
        		answer *= ++count[i];
        	}

        	return answer-1;    
        }
        ```
---
- 임수환
    - 완주하지 못한 선수

        ```cpp
        #include <string>
        #include <vector>
        #include <map>
        using namespace std;

        string solution(vector<string> participant, vector<string> completion) {
            string answer = "";

            map<string, int> ans;
            
            for(string s: completion) == for(int s = 0; s < completion.size(); s++)
                ans[s] += 1;
          
            for(string s: participant) {
                ans[s] -= 1;
                if(ans[s] < 0){
                    answer = s;
                    break;
                }
            }
            
            return answer;
        }

        string hash_function(string key) {
        		return key;
        }
        ```

    - 전화번호 목록

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>

        using namespace std;

        bool solution(vector<string> phone_book) {
            bool answer = true;
            
            sort(phone_book.begin(), phone_book.end());
            for(int i = 0; i < phone_book.size() - 1; i++) {
                if(phone_book[i+1].compare(0, phone_book[i].length(), phone_book[i]) == 0) return false;
            }     
            return answer;
        }
        ```

    - 위장

        ```cpp
        #include <string>
        #include <vector>
        #include <map>
        using namespace std;

        int solution(vector<vector<string>> clothes) {
            int answer = 1;
            
            map<string, int> ans;
            
            
            for(int i = 0; i < clothes.size(); i++){
                ans[clothes[i][1]] ++;   
            }
            
            for(pair<string, int> i: ans)
                answer = answer * (i.second + 1);
            
            answer--;
            
            return answer;
        }
        ```