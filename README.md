# SDH - LAB 5 - Zuccolo Giada, matr. 2055702

## PROCEDURE >> HTTP

- On wireshark, start the capture

- go to (HTTP) page: http://www.w3bai.com/it/html/tryit.php?filename=tryhtml_form_submit_id

- Set the form like this:

  ```html
  <!DOCTYPE html>
  <html>
  <body>
  
  <form action="action_page.php" method="get">
    Input name:<br>
    <input type="text" name="input_name">
    <br><br>
    <input type="submit" value="Submit">
  </form> 
  
  </body>
  </html>
  ```

  

- submit the form with "Giada Zuccolo" as value 

- modity again the form with `method="post"`

- submit the form with "Giada Zuccolo" as value 

- Stop capture in Wireshark

- In Wireshark set filter `http.request.method=="GET"`

- → check result in wireshark (No. 224)

- In Wireshark set filter `http.request.method=="POST"`

- → check result in wireshark (No. 578)

WIRESHARK FILE: 

## PROCEDURE >> HTTPS

### GET

- Work with **uniweb** login (https://uniweb.unipd.it/Home.do)

- Start capture in Wireshark

- Click on login (HTTPS) page https://shibidp.cca.unipd.it/idp/profile/SAML2/Redirect/SSO?execution=e4s1

- Obviously this form works with `method="post"`
  → so with the function of "analyze page", I changed this parameter, setting `method="get"` first

- Submit the form

  **An interesting note:** 
  This was the resulting page: 
  ![](C:\Users\giada\Desktop\Senza nome.png)

  And this was the URL: https://shibidp.cca.unipd.it/idp/profile/SAML2/Redirect/SSO?j_username=giada.zuccolo%40studenti.unipd.it&j_username_js=giada.zuccolo&dominio=%40studenti.unipd.it&j_password=*"plaintext password"* **<u>&_eventId_proceed=</u>**

- Stop capture in Wireshark

### POST

- Work again **uniweb** login
- Start capture in Wireshark
- go to HTTPS page https://shibidp.cca.unipd.it/idp/profile/SAML2/Redirect/SSO?execution=e4s1
- This time I left the `method="post"` parameter in the form first
- Submit the form
- Stop capture in Wireshark

### WIRESHARK: some comments

In HTTPS case, I have to filter with `ssl filter` to see some results.
I also looked directly for the package with the additional filters that wireshark offers. For example set to search for the string `shibidp.cca.unipd.it` or the string `uniweb.unipd.it` in the package details.
