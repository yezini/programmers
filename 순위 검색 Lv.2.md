```java

class Solution {
    
    HashMap<String, ArrayList<Integer>> hashMap = new HashMap<>(); // 만약 query에 해당하는 값이 ---- 이라는 키가 만들어지면 전체를 의미 
    ArrayList<Integer> score = new ArrayList<>();
    
    public int[] solution(String[] info, String[] query) {
        int[] answer = new int[query.length];
        
        // 지원자 모든 정보의 해시맵 만들기
        for (String a : info) {
            dfs(0, "", a.split(" "));
        }
        
        // 해시맵 값의 리스트들을 오름차순으로 정렬  
        for (ArrayList<Integer> list : hashMap.values()) {
            Collections.sort(list);
        }
        
        int i = 0; //쿼리반복횟수 및 answer[i] 
        for (String q : query) { // "java and backend and junior and pizza 100"
            String[] data = q.split(" and "); // [java,backend,junior,pizza 100]

            String[] s = data[3].split(" "); // [pizza,100] 
            int target = Integer.parseInt(s[1]); // 100점 
            data[3] = s[0]; // pizza 100 -> pizza
            
            // data = [java,backend,junior,pizza]
            String key = String.join("", data); // javabackendjuniorpizza

            if (hashMap.containsKey(key)) {
                ArrayList<Integer> list = hashMap.get(key);
                int start = 0;
                int end = list.size() - 1;

                while (start <= end) {
                    int mid = (start + end) / 2;

                    if (list.get(mid) < target) {
                        start = mid + 1;
                    }else{
                        end = mid - 1;
                    }
                }

                answer[i] = list.size() - start;
            }
            i++;
        }
        
        return answer;
    }
}

```
