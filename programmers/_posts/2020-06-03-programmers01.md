---
layout: post
title: 해시
---

# 해시

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

    - 베스트앨범

        ```python
        genres = ['classic', 'pop', 'classic', 'classic', 'pop']
        plays = [500, 600, 150, 800, 2500]
        dic1 = {}
        dic2 = {}
        temp = 0
        for num in plays:
            order[num]=tem
            tem +=1
        for i in genres:
            dic1[i] = 0
            dic2[i] = 0
        for i in genres:
            if dic1[i]<plays[temp]:
                dic2[i]=dic1[i]
                dic1[i]=plays[temp]
                temp+=1
                continue
                
            if dic2[i]<plays[temp]:
                dic2[i]=plays[temp]
                temp+=1
                continue
                
        print(dic1)
        print(dic2)
        ```

        ```
        {'classic': 800, 'pop': 2500}
        {'classic': 500, 'pop': 600}
        ```

        실패~~ tuple 내에 고유번호가 추가되는 식 혹은 해쉬 함수를 사용해서 순서를 파악하는 것이 추가로 필요할 듯 하다

    - 
- 정효인
    - 완주하지 못한 선수(50점→100점)

        ```cpp
        #include <string>
        #include <vector>

        using namespace std;

        int Hash(vector<string> p, vector<string> c);

        string solution(vector<string> participant, vector<string> completion) {
            int index = Hash(participant, completion);
            
            string answer = participant.at(index);
            return answer;
        }
        int Hash(vector<string> p, vector<string> c)
        {
            for(int i=0;i<p.size();i++)
            {
                for(int j=0;j<c.size();j++)
                {
                    if(p[i]==c[j])
                    {
                        c[j]="0";
                        break;
                    }
                    if(j==(c.size()-1))
                    {
                        if(p[i]!=c[j])
                        return i;
                    }
                }
            }
        }
        ```

        답은 다 맞았는데 속도 초과로 인한 50점
        아직 c++를 익히고 있고, 후에 STL을 배우면 다시 풀어보겠음

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        int Hash(vector<string> p, vector<string> c);

        string solution(vector<string> participant, vector<string> completion) {
            sort(participant.begin(), participant.end());
            sort(completion.begin(), completion.end());
            int index = Hash(participant, completion);
            
            string answer = participant[index];
            return answer;
        }

        int Hash(vector<string> p, vector<string> c)
        {
            sort
            
            for(int i=0;i<c.size();i++)
            {
                if(p[i] != c[i])
                {
                    return i;
                }
            }
            return p.size()-1;
        }
        c++
        ```

        의문점: Hash함수 안에 sort 넣었더니 다른 답이나옴.
        반면에 main함수(solution)에서 sort하면 답이 나옴.

        ㄴ 해결

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        int Hash(vector<string> p, vector<string> c);

        string solution(vector<string> participant, vector<string> completion) {
        	int i;
        	sort(participant.begin(), participant.end());
            sort(completion.begin(), completion.end());
            for(i=0;i<participant.size();i++)
            {
                if(participant[i] != completion[i])
                {
                    return participant[i];
                }
            }
            return participant[i];
        }
        ```

        모범 답안의 기준이 무엇인가?  해시 자료구조를 이용했다는 것을 잘 보여주면 되는건지, 코드가 간단하면 할수록 그것이 모범답안인지, 정해서 다음부터 발표해야할 필요성이 있는 거 같음.

    - 전화번호 목록(100점)

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        bool solution(vector<string> phone_book) {
            sort(phone_book.begin(),phone_book.end());
            for(int i=0;i<phone_book.size()-1;i++)
            {
                for(int j=i+1;j<phone_book.size();j++)
                {
                    if(phone_book[i].compare(phone_book[j].substr(0,phone_book[i].size()))==0)
                    {
                        return false;
                    }
                }
            }
            bool answer = true;
            return answer;
        }
        ```

        ```jsx
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        bool solution(vector<string> phone_book) {
            sort(phone_book.begin(),phone_book.end());
            for(int i=0;i<phone_book.size()-1;i++)
            {
        		if(phone_book[i].compare(phone_book[i+1].substr(0,phone_book[i].size()))==0)
                {
                    return false;
                }
            }
            bool answer = true;
            return answer;
        }
        ```

        사실 해시문제를 풀면서 느끼는 점이지만, solution 함수를 작성하는 것이 hash function을 구현하는 것이라고 생각한다. hash function = solution, key = solution 함수 입력 인자, index = 0 or 1, value = 0 or 1.

    - 위장

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        int main(vector<vector<string>> clothes) {
            int count = 1;
            int answer = 1;
            vector<int> c(30);
            for(int i = 0; i < clothes.size(); i++)
            {
                for(int j = 0; j <  clothes[i].size(); j++)
                {
                    iter_swap(clothes[i].begin(),clothes[i].end());
                }
            }
            sort(clothes.begin(),clothes.end());
            for(int i=0;i<clothes.size();i++)
            {
                if(clothes[i].begin()==clothes[i+1].begin())
                {
                    count++;
                }
                else
                {
                    c.push_back(count+1);
                    count = 1;
                }
            }
            c.push_back(count+1);
            for(int j = 0;j< c.size();j++)
            {
                answer*=c[j];
            }
            return (answer-1);
        }
        ```

        without unordered_map. (컴파일 오류)

        ```cpp
         if(clothes[i].begin()==clothes[i+1].begin())
        ```

        이부분 때문. vector에 익숙치 않아서 스왑을 일일이 해주는 것이 불편하다

        ```cpp
        #include <string>
        #include <vector>
        #include <algorithm>
        using namespace std;

        int solution(vector<vector<string>> clothes) {
            int answer = 1;
            int count = 1;
            for(int i = 0; i < clothes.size(); i++)
        	{
        		swap(clothes[i][0],clothes[i][1]);
        	}
        	sort(clothes.begin(),clothes.end());
            for(int i=0;i<clothes.size();i++)
        	{
        		if(i==clothes.size()-1)
        		{
        			++count;
        			continue;
        		}
        		if(clothes[i][0]!=clothes[i+1][0])
        		{	
        			answer *= ++count;
        			count = 1;
        		}
        		else
        		{
        			++count;
        		}
                
        	}
        	answer*=count;
            return answer-1;
        }
        ```

        끈기로 품

        ```cpp
        #include <string>
        #include <vector>
        #include <unordered_map>
        using namespace std;

        int solution(vector<vector<string>> clothes) {
            int answer = 1;
            unordered_map<string, int> hash_map;
            for(auto cloth: clothes)
            {
                hash_map[cloth[1]]++;
            }
            for(auto iter =  hash_map.begin();iter != hash_map.end(); iter++)
            {
                answer *= (iter->second+1);
            }
            return answer-1;
        }
        ```

        hash 이용

    - 베스트앨범

        ```cpp
        #include <string>
        #include <vector>
        #include <map>
        #include <algorithm>
        #include <iostream>

        using namespace std;
        bool cmp(const pair<string,int>& a,const pair<string,int>& b)
        {
            return a.second > b.second;
        }

        vector<int> solution(vector<string> genres, vector<int> plays) {
            vector<int> answer;
        	vector<int> value;
        	vector<int> answervalue;
            vector<string> Sgenres(genres);
            multimap <string,int> hashmap;
            map <string,int> shashmap;
            for(int i=0;i<genres.size();i++)
            {
                hashmap.insert(pair(genres[i],plays[i]));
            }
          
            sort(Sgenres.begin(),Sgenres.end());
            Sgenres.erase(unique(Sgenres.begin(),Sgenres.end()),Sgenres.end());
            multimap<string,int>::iterator iter;
            for(int i=0;i<Sgenres.size();i++)
            {
                int sum=0;
                for(iter=hashmap.lower_bound(Sgenres[i]);iter!=hashmap.upper_bound(Sgenres[i]);iter++)
                {
                   sum+=(iter->second);
                }
                shashmap[Sgenres[i]]=sum;
            }
            vector<pair<string,int>> vec(shashmap.begin(), shashmap.end());
            sort(vec.begin(),vec.end(),cmp);
            for(int i=0;i<Sgenres.size();i++)
            {
                int count=0;
                for(iter=hashmap.lower_bound(vec[i]);iter!=hashmap.upper_bound(vec[i]);iter++)
                {
                   if(count==2)
        		   {
        			   break;
        		   }
        			answervalue.push_back(iter->second);
        			count++;
                }
                
            }
        	for(int i=0;i<answervalue.size();i++)
        	{
        		answer.push_back(find(answervalue.begin(),answervalue.end(),answervalue[i]));
        	}
            return answer;
        }
        ```

    - 

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
