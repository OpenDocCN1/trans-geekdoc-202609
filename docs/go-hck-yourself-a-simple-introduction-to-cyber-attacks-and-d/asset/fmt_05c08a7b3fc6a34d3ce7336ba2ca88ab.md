
125. [118](#c09.xhtml#Page_118)
126. [119](#c09.xhtml#Page_119)
127. [120](#c09.xhtml#Page_120)
128. [121](#c09.xhtml#Page_121)
129. [122](#c09.xhtml#Page_122)
130. [123](#c09.xhtml#Page_123)
131. [125](#c10.xhtml#Page_125)
132. [126](#c10.xhtml#Page_126)
133. [127](#c10.xhtml#Page_127)
134. [128](#c10.xhtml#Page_128)
135. [129](#c10.xhtml#Page_129)
136. [130](#c10.xhtml#Page_130)
137. [131](#c10.xhtml#Page_131)
138. [132](#c10.xhtml#Page_132)
139. [133](#c10.xhtml#Page_133)
140. [134](#c10.xhtml#Page_134)
141. [135](#c11.xhtml#Page_135)
142. [136](#c11.xhtml#Page_136)
143. [137](#c11.xhtml#Page_137)
144. [138](#c11.xhtml#Page_138)
145. [139](#c11.xhtml#Page_139)
146. [140](#c11.xhtml#Page_140)
147. [141](#b01.xhtml#Page_141)
148. [142](#b01.xhtml#Page_142)
149. [143](#b01.xhtml#Page_143)
150. [144](#b01.xhtml#Page_144)
151. [145](#b01.xhtml#Page_145)
152. [147](#b02.xhtml#Page_147)
153. [148](#b02.xhtml#Page_148)
154. [149](#b02.xhtml#Page_149)
155. [150](#b02.xhtml#Page_150)
156. [151](#b02.xhtml#Page_151)
157. [153](#b03.xhtml#Page_153)
158. [154](#b03.xhtml#Page_154)
159. [155](#b03.xhtml#Page_155)
160. [156](#b03.xhtml#Page_156)
161. [157](#b03.xhtml#Page_157)
162. [158](#b03.xhtml#Page_158)
163. [159](#b03.xhtml#Page_159)
164. [160](#b03.xhtml#Page_160)
165. [164](#b03.xhtml#Page_164)

# Go H\*ck Yourself

Copyright © 2022 by Bryson Payne.

All rights reserved. No part of this work may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without the prior written permission of the copyright owner and the publisher.

Printed in the United States of America

First printing

25 24 23 22 21 1 2 3 4 5 6 7 8 9

ISBN-13: 978-1-7185-0200-0 (print)
ISBN-13: 978-1-7185-0201-7 (ebook)

Publisher: William Pollock
Managing Editor: Jill Franklin
Production Manager: Rachel Monaghan
Production Editor: Paula Williamson
Developmental Editor: Nathan Heidelberger
Cover Design: Monica Kamsvaag
Interior Design: Octopod Studios
Technical Reviewer: Bryan Fagan
Copyeditor: Paula Fleming
Compositor: Maureen Forys, Happenstance Type-O-Rama
Proofreader: Scout Festa
Indexer: JoAnne Burek

For information on book distributors or translations, please contact No Starch Press, Inc. directly:
No Starch Press, Inc.
245 8th Street, San Francisco, CA 94103
phone: 1.415.863.9900; info@nostarch.com
www.nostarch.com

*Library of Congress Cataloging-in-Publication Data*

Names: Payne, Bryson, author.
Title: Go h\*ck yourself : a simple introduction to cyber attacks and defense
   / Bryson Payne.
Other titles: Go hack yourself
Description: San Francisco : No Starch Press, \[2021\] | Includes index.
Identifiers: LCCN 2021030107 (print) | LCCN 2021030108 (ebook) | ISBN
   9781718502000 (print) | ISBN 9781718502017 (ebook)
Subjects: LCSH: Penetration testing (Computer security)
Classification: LCC QA76.9.A25 P394 2021 (print) | LCC QA76.9.A25 (ebook)
   | DDC 005.8—dc23
LC record available at https://lccn.loc.gov/2021030107
LC ebook record available at https://lccn.loc.gov/2021030108

No Starch Press and the No Starch Press logo are registered trademarks of No Starch Press, Inc. Other product and company names mentioned herein may be the trademarks of their respective owners. Rather than use a trademark symbol with every occurrence of a trademarked name, we are using the names only in an editorial fashion and to the benefit of the trademark owner, with no intention of infringement of the trademark.

The information in this book is distributed on an “As Is” basis, without warranty. While every precaution has been taken in the preparation of this work, neither the author nor No Starch Press, Inc. shall have any liability to any person or entity with respect to any loss or damage caused or alleged to be caused directly or indirectly by the information contained in it.

To Bev, Alex, and Max: Everything I write is for you.

## About the Author

Dr. Bryson Payne is an award-winning cyber coach, author, and TEDx speaker, and the founding director of the Center for Cyber Operations Education at the University of North Georgia, an NSA-DHS Center for Academic Excellence in Cyber Defense. He is a tenured professor of computer science at UNG, where he has taught aspiring coders and cyber professionals since 1998, including coaching UNG’s #1-in-the-nation NSA Codebreaker Challenge cyber operations team. In 2017, he received the University System of Georgia Chancellor’s Service Excellence Leader of the Year Award. He has also been awarded the Department of the Army Commander’s Award for Public Service medal from US Army Cadet Command and the Order of Thor medal from the Military Cyber Professionals Association. Dr. Payne was also recognized by the UNG Alumni Association as the 2021 Distinguished Professor.

Dr. Payne is a Certified Information Systems Security Professional (CISSP) and Certified Ethical Hacker (CEH), and he holds the elite SANS|GIAC GPEN, GRID, and GREM certifications. He has written over $45 million in successful grants for workforce development, technology education, and cybersecurity, and he has trained over 60,000 students through his online courses on coding and ethical hacking, including three top-rated Udemy courses. He was also the first department head of computer science at UNG and enjoys working with K–12 schools worldwide to promote computer science and cybersecurity education.

Dr. Payne holds a PhD in computer science from Georgia State University. Featured in the *Wall Street Journal*, *Campus Technology*, and *CIO* magazine, he is also the author of *Teach Your Kids to Code* and *Learn Java the Easy Way*, both published by No Starch Press. He has been programming, hacking, and reverse-engineering software for over 36 years; he sold his first paid program to *RUN Magazine* (Commodore 64) for its “Magic” column in 1985, for $10. In addition to his love for technology, Dr. Payne enjoys learning languages and speaks Spanish, French, Russian, and Mandarin Chinese.

## About the Technical Reviewer

Bryan Fagan is a coding enthusiast living in Dahlonega, Georgia, where he spends most of his time teaching high school students about cybersecurity. He has started several afterschool programs focused on engineering, technology, and digital game design.

## Acknowledgments

Special thanks to the team at No Starch Press for helping make this book a reality: Bill Pollock, Nathan Heidelberger, Barbara Yien, Dapinder Dosanjh, Liz Chadwick, Jennifer Kelley, Matthew Kim, Annie Choi, Janelle Ludowise, Laurel Chun, Athabasca Witschi, Rachel Monaghan, JoAnne Burek, Lisa Devoto Farrell, Derek Yee, Paula Fleming, and Paula Williamson.

Thanks to my long-time colleague, fellow educator, and friend, Bryan Fagan, for his thoughtful and thorough technical review across all the changes in Kali Linux and most of the hacking tools over the past two years.

Thanks to my mom, Esta, for buying me that Commodore 64 in the early 1980s and encouraging me to pursue my dreams—I never knew how far coding and hacking would take me. Thanks to my father-in-law, Norman, for always having time to talk computers with me. And thanks most of all to my beautiful wife, Bev, and my sons, Alex and Max, for their love and support as I wrote this third book—thanks especially for making me take breaks to jump on the trampoline, do science experiments, play games, watch movies, and swim. This book, and my life, are infinitely better and more fun thanks to you.

## Introduction

![](image_fi/book_art/chapterart.png)
