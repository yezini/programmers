```java
import java.util.*;
// info와 query의 값을 하나씩 비교하면 시간 초과가 나기 때문에 info가 포함될 수 있는 모든 값을 map에 key로 넣고 점수를 value에 넣으며 해시맵 생성 
class Solution {

    static HashMap<String, ArrayList<Integer>> hashMap = new HashMap<>(); // 만약 query에 해당하는 값이 ---- 이라는 키가 만들어지면 전체를 의미
    static ArrayList<Integer> score = new ArrayList<>();

    public int[] solution(String[] info, String[] query) { // 지원자 정보와 조건 정보
        int[] answer = new int[query.length];

        // 지원자 모든 정보의 해시맵 만들기 (-를 포함한 모든 경우의 수 만들기)
        for (String a : info) {
            dfs(0, "", a.split(" "));
        }

        // 해시맵 값의 리스트들을 오름차순으로 정렬 -> 정렬을 통한 이분탐색을 통해 원하는 점수 이상인 것을 더 빠르게 뽑아냄 
        for (ArrayList<Integer> list : hashMap.values()) {
            Collections.sort(list);
        }

        int i = 0;
        for (String q : query) { // "java and backend and junior and pizza 100"
            String[] data = q.split(" and "); // [java,backend,junior,pizza 100]

            String[] s = data[3].split(" "); // [pizza,100]
            int target = Integer.parseInt(s[1]); // 100
            data[3] = s[0]; // pizza 100 -> pizza
            // data = [java,backend,junior,pizza]

            String key = String.join("", data); // javabackendjuniorpizza

              if (hashMap.containsKey(key)) { // 해쉬맵이 조건 정보를 가지고 있다면
                ArrayList<Integer> list = hashMap.get(key); // 해쉬맵 키로 값(점수)을 구한 후 배열 생성 
                int start = 0;
                int end = list.size() - 1;

                while (start <= end) {
                    int m = (start + end) / 2;

                if (list.get(m) < target) {
                        start = m + 1;
                }else{
                        end = m - 1;
                }
                }        

                answer[i] = list.size() - start; // target 보다 큰 값이 처음 나오는 경우를 찾아 전체 크기에서 해당 위치 빼기
               }
            i++;
        }
        return answer;
    }

    static void dfs(int depth, String query, String[] info) {

        if(depth == 4){ // 즉, 점수에 해당하는 부분
            if (!hashMap.containsKey(query)) {
                score = new ArrayList<>();
                score.add(Integer.parseInt(info[4]));
                hashMap.put(query, score);
                }else{
                hashMap.get(query).add(Integer.parseInt(info[4]));
                }
            return;
            }

            dfs(depth + 1, query + "-", info);
            dfs(depth + 1, query + info[depth], info);
    }
}

```
