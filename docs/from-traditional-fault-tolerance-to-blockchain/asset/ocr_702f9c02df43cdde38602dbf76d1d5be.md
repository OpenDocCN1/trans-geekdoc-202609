To increase the chance of delivery during replay, the bounce message is deferred.

On the IMAP side, the consistency test is based on the comparison of the externalized state as the result of a verb. The externalized state includes the following:

+   - The email message itself (the text and the attachments, if any) if one is fetched.
+   - The list of email headers, such as To, From, Cc, and Subject, for verbs that involve listing of emails.
+   - The list of folders for verbs that requested them.
+   - Execution status for verbs that modify the state of the email system.

The consistency test would declare inconsistency if any part of the externalized state is missing or different during replay compared with that of the original execution. For most verbs, when the consistency test fails, the compensation method inserts an explanatory message into the user’s Inbox stating the reasons for the discrepancy.

# REFERENCES

+   1. R. Bianchini, R. P. Martin, K. Nagaraja, T. D. Nguyen, and F. Oliveira. Human-aware computer system design. In Proceedings of the 10th conference on Hot Topics in Operating Systems - Volume 10, HOTOS'05, pages 13–13, Berkeley, CA, USA, 2005. USENIX Association.
+   2. D. M. Blough and A. Pelc. Diagnosis and repair in multiprocessor systems. IEEE Trans. Comput., 42(2):205–217, Feb. 1993.
+   3. P. Bodik, A. Fox, M. I. Jordan, D. Patterson, A. Banerjee, R. Jagannathan, T. Su, S. Tenginakai, B. Turner, and J. Ingalls. Advanced tools for operators at amazon.com. In Proceedings of the First international conference on Hot topics in autonomic computing, HotACI'06, pages 1–1, Berkeley, CA, USA, 2006. USENIX Association.
+   4. A. Brown and D. Patterson. To err is human. In Proceedings of the 2001 Worshop on Evaluating and Architecting System Dependability, Gteborg, Sweden, 2001.
+   5. A. B. Brown and D. A. Patterson. Rewind, repair, replay: three r’s to dependability. In Proceedings of the 10th workshop on ACM SIGOPS European workshop, EW 10, pages 70–77, New York, NY, USA, 2002. ACM.
+   6. A. B. Brown and D. A. Patterson. Undo for operators: building an undoable e-mail store. In Proceedings of the annual conference on USENIX Annual