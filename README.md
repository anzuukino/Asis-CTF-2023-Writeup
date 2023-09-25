# Asis-CTF-2023-Writeup
# Bài 1 hello:
- Tóm tắt đề thì đại khái là đề bảo chúng ta phải request mỗi cái method get có parameter là x lên Web sao cho không có chữ next và chữ file là được, nhưng mà muốn đọc được flag thì phải đọc được file next.txt
- Đọc đề thì mình thấy người ta cho hint là đi đọc cái manpage curl đi, thì oke mình cũng đi đọc
![Screenshot 2023-09-25 082235](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/7ae2fa24-1f2a-488d-aec3-16dc969752b7)
- Sau 2 tiếng đọc manpage ( không tính thời gian chơi csgo <(") ) thì mình cũng hiểu ra vấn đề chúng ta có thể tận dụng cái này
![Screenshot 2023-09-25 082723](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/4ca2f9ea-6be0-4316-bce4-9d516d02797f)
- Đây là payload của mình **?x=f[a-i]le:///ne[b-x]t.txt**
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/016a706a-2952-4865-a600-25ac49ddf104)
- Nó hiện ra một đường dẫn khác mình vào xem thử
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/61c1b8f1-4841-420a-bde5-04cb32fb5ec7)
- Theo hướng dẫn mình cũng làm theo
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/cddde8df-38cc-41cf-b6a9-f14ac0cea946)
- Decode Base64 ra thì nó cho mình cái này
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/cd8f4e99-9fc6-47b4-b7d8-8b5f30f53569)
- Chắc chắn **/app/index.js** là source nên mình tìm cách để xem nó và đây là source của nó
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/baded8ba-ac9f-4fea-8504-2089b7fa7465)
- Decode tiếp thì ra source code
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/1c7fa903-5a9d-4cba-ae1d-74c0dc6e69a7)
- Code này đại khái là cũng như cái đầu bắt mình đọc file /next.txt nhưng lại cấm chữ next
- Đến đoạn này thì mình khá là ngu ngồi đọc source lui tới xong tự nhiên mình nhận ra lỗi ở 2 chổ này
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/6f36ec0b-73c3-4fba-acd3-a281c789a29c)
- **path.basename(fpath)** sẽ trả lại cái tên file về cho mình còn **fs.readFileSync(fpath)** sẽ đọc file của fpath
- Sau một số thử nghiệm thì đây là payload cuối cùng của mình **/next.txt%00/yuu.txt**
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/0d756daa-d3fc-483d-9e47-ddb42fb5a627)
- Decode cái nữa
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/5c4c38f8-a2a5-4dab-86e7-26bfb44a148f)
- Đoạn này mình đã định đấm máy rồi xong decode cái nữa thì rất là yêu đời
![image](https://github.com/Yuu2311/Asis-CTF-2023-Writeup/assets/86243871/446dd52b-5567-4af4-98be-fa0192cd49b6)
- Flag: **ASIS{good_job_bun}**
- ~~Mấy bài còn lại mình chịu nha <(")~~








