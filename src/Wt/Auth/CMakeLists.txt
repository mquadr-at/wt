SUBDIRS(Dbo)
IF(INSTALL_EXTENSIONLESS_HEADERS)
  INSTALL_FILES(/include/Wt/Auth "^[^bD.][^.]+[^hC~]$")
ENDIF(INSTALL_EXTENSIONLESS_HEADERS)

FILE(GLOB AUTH_H_FILES RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.h")
LIST(REMOVE_ITEM AUTH_H_FILES MailUtils.h passwdqc.h)
INSTALL(FILES ${AUTH_H_FILES}
        DESTINATION include/Wt/Auth)

IF(INSTALL_EXTENSIONLESS_HEADERS)
  INSTALL_FILES(/include/Wt/Auth "^PasswordHash$")
ENDIF(INSTALL_EXTENSIONLESS_HEADERS)

IF (ASCIIDOC_FOUND)
  ASCIIDOC_FILE(auth-tutorial
    ${CMAKE_SOURCE_DIR}/doc/tutorial/auth.doc
    ${CMAKE_SOURCE_DIR}/doc/tutorial/auth.html)
ENDIF (ASCIIDOC_FOUND)
