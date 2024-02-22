```java

class Solution {
    public int solution(String[] board) {
        int o_cnt = 0;
        int x_cnt = 0;
        //O, X 개수
        for (int i = 0; i < 3; i++) {
            o_cnt += test(board[i], 'O');
            x_cnt += test(board[i], 'X');
}

        //X가 O보다 많으면 안됨(O가 선공)
        if (x_cnt > o_cnt) {
            return 0;
}

        //O가 X보다 2개이상 많으면 안됨
        if (o_cnt > x_cnt + 1) {
            return 0;
}

        //O가 완성 되었는데 X가 O의 개수와 같으면 안됨(O가 완성되었으면 경기 종료)
        if (win(board, 'O')) {
            if (o_cnt == x_cnt) {
                return 0;
}
        }
        //X가 완성 되었는데 O가 X보다 1개 많으면 안됨
        if (win(board, 'X')) {
            if (o_cnt == x_cnt + 1) {
                return 0;
}
        }
        return 1;//해당 경우가 아니면 1 리턴
}

    private static int test(String str, char chr) {
        return str.length() - str.replace(String.valueOf(chr), "").length();
}

    private static boolean win(String[] board, char chr) {
        //가로
        for (int i = 0; i < 3; i++) {
            if (board[i].charAt(0) == chr && board[i].charAt(1) == chr && board[i].charAt(2) == chr) {
                return true;
}
        }
        //세로
        for (int i = 0; i < 3; i++) {
            if (board[0].charAt(i) == chr && board[1].charAt(i) == chr && board[2].charAt(i) == chr) {
                return true;
}
        }
        //대각선
        if (board[0].charAt(0) == chr&& board[1].charAt(1) == chr&& board[2].charAt(2) == chr) {
            return true;
}
        //대각선
        if (board[0].charAt(2) == chr&& board[1].charAt(1) == chr&& board[2].charAt(0) == chr) {
            return true;
}
        return false;
}
}

```
