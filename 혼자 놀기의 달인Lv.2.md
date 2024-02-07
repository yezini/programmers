```java
import java.util.*;

class Solution {
    public int solution(int[] cards) {
        int n = cards.length;
        
		int[][] r = new int[n][n]; // 상자를 열었을 때 다음 상자로 이동
		for (int i = 0; i < n; i++) {
			r[i][cards[i] - 1] = 1;
		}

	PriorityQueue<Integer> cnts = new PriorityQueue<>(Collections.reverseOrder());
		for (int i = 0; i < n; i++) {
			if (r[i][cards[i] - 1] == 1) {
				// 상자 경로
				int r1 = i;
				int r2 = cards[i] - 1;

				// 연 상자의 개수
				int cnt = 0;

				while (r[r1][r2] != 0) {
					// 현재 상자 열기
					r[r1][r2] = 0;

					// 연 상자의 개수 증가
					cnt++;

					// 다음 상자의 경로 저장
					r1 = r2;
					r2 = cards[r1] - 1;
				}

				// 연 상자의 개수 저장
				cnts.add(cnt);
			}
		}

		// 1번 상자 그룹을 제외하고 남는 상자가 없으면 0점
		if (cnts.size() == 1)
			return 0;

		// 1번 상자 그룹에 속한 상자의 수와 2번 상자 그룹에 속한 상자의 수를 곱하기
		// 상자의 수가 가장 많은 두 그룹을 선정
		int group1= cnts.poll();
		int group2= cnts.poll();
		return group2 * group1;
    }
}
```
