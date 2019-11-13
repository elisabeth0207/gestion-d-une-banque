 
import sys

compte = None
user = None
password = None

class Guichetier:
    def __init__(self, reponse):
        self.reponse = reponse
        while True:
            self.login = Connexion()
            if self.login.login() == True:
                print('Vous vous etes bien connecte !!!')
                print('------------------------------------------------')
                break
            else:
                print('Erreur de connexion')
                respon = input('Avez vous un compte(o/n): ')
                if respon == 'o':
                    print('------------------------------------------------')
                    print('Essayez a nouveau !!!')
                elif respon == 'n':
                    print('On va geres ce cas avec la BD!!')
                    #compte, user, password = Controleur()

        self.run()

    def versement(self):
        somme = input('Quelle somme voulez vous verser: ')
        print('Vous avez fait un versement de {} XAF'.format(somme))


    def retrait(self):
        somme = input('Quelle somme voulez vous retirer: ')
        while True:
            confirm = input('Pour des raisons de securite veillez confirmer avec votre mot de passe: ')

            if confirm == self.login.password:
                print('Retrait de {} effectue avec succes!!'.format(somme))
                break
            else:
                print('Vos identifiants ne sont pas correct !!!')



    def virement(self):
        beneficiare = input('Entrez le numero de compte du beneficiare: ')
        somme = input('Combien voulez vous virer: ')
        print('Vous allez faire un virement de {} au compte {} !!!'.format(somme, beneficiare))


    def international(self):
        pays = input('Entrez le nom du pays: ')
        beneficiare = input('Entrez le numero de compte du beneficiare: ')
        somme = input('Combien voulez vous virer: ')
        print('Vous allez faire un virement de {} au compte {} !!!'.format(somme, beneficiare))

    def run(self):
        if self.reponse == 1:
            self.versement()
        elif self.reponse == 2:
            self.retrait()
        elif self.reponse == 3:
            self.virement()
        elif self.reponse == 4:
            self.international()
        print('------------------------------------------------')


class Compte:
    def __init__(self):
        self.solde = 0

class Controleur:
    def __init__(self):
        self.run()

    def ajouterCompte(self):
        print('1 - compte courant')
        print('2 - compte epargne')
        self.compte = input('Quel type de compte voulez vous creer: ')
        if compte == 1:
            self.name = input('Entrez votre nom: ')
            self.password = input('Entrez votre password: ')
            return self.compte, self.name, self.password
        elif compte == 2:
            self.name = input('Entrez votre nom: ')
            self.password = input('Entrez votre password: ')
            return self.compte, self.name, self.password

    def supprimerCompte(self):
        pass

    def modifierCompte(self):
        pass

    def saveInfoEmprunt(self):
        pass

    def run(self):
        print('1- Creer un compte')
        print('2- Creer un supprimerCompte')
        print('3- Creer un modifierCompte')

        reponse = int(input('Que voulez faire: '))
        if reponse == 1:
            compte, user, password = self.ajouterCompte()
            return compte, user, password


class Client:
    def __init__(self, name, numeroCompte):
        self.name = name
        self.numeroCompte = numeroCompte

class Connexion:
    def __init__(self):
        self.name = input('Votre login: ')
        self.password = input('Votre password: ')
        self.login()

    def login(self):
        if self.name == 'felix' and self.password == 'felix':
            return True
        else:
            return False

if __name__ == "__main__":
    print('# -- Bien venu a la banque L2IN -- #', end='\n')

    while True:
        print('1- Faire un versement')
        print('2- Faire un retrait')
        print('3- Faire un virement')
        print("4- Faire un virement a l'international")
        print('0- Quitter')

        reponse = int(input('Que voulez vous faire: '))
        
        if reponse == 0:
            sys.exit()

        Guichetier(reponse)
    

    
