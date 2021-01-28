package user;
/*
 * 데이터 베이스 접근 클래스
 */
//ctrl + shift + o 를 통해 한번에 생성
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

public class UserDAO {

	private Connection conn; //데이터베이스에 접근해주는 객체
	private PreparedStatement pstmt;
	private ResultSet rs; //어떤한 정보를 담을수 있는 개체

	public UserDAO() { //실제 MYSQL에 접속하게 해주는 부분
		 try {
			 String dbURL = "jdbc:mysql://localhost:3306/BBS";
			 //3306은 PC에 설치된 MYSQL 서버 번호
			 String dbID ="root";
			 String dbPassword = "taeyoon!";
			 Class.forName("com.mysql.jdbc,Driver");
			 conn = DriverManager.getConnection(dbURL, dbID, dbPassword);
		 } catch(Exception e) {
			 e.printStackTrace();//오류 발생할 경우 오류 출력
		 }
	}
	
	public int login(String userID, String userPassword) {
		String SQL = "SELECT userPassword FROM USER WHERE userID = ?";
		try {
			pstmt = conn.prepareStatement(SQL);
			pstmt.setNString(1, userID);
			rs = pstmt.executeQuery();
			if(rs.next()) {//결과가 존재한다면
				if(rs.getString(1).equals(userPassword)) {
					return 1; //로그인 성공
				}
				else
					return 0; //비밀번호 불일치
			}
			return -1; //아이디가 없음
		}catch (Exception e) {
			e.printStackTrace();
		}
		return -2;//데이터 베이스 오류 의미
	}
}
