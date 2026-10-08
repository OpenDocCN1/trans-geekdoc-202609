# #8 C# portfolio pricing application

# ## 8.1 Introduction

This section provides details concerning a C# application, created using Microsoft Visual Studio 2005 (version 2.0), which values the deals contained in a set of user specified portfolios. It has been included to illustrate how the kind of software that may be found in a bank, financial institution, or educational establishment. can be incorporated into the technical skills required in the previous sections of the book can be discussed. Here we provide code excerpts from the application; however, additional source code is available from the publisher's website.
The main features of this application are as follows:

+   - User defined portfolios of deals can be valued without the need to compile either C or C# programs. This application is easy to use and accessible to those who possess business or financial knowledge, but do not have the technical skills required to write computer code.
- This application only deals with equity, foreign exchange derivatives—the exception is the inclusion of an interest rate forward rate. However, the software can be easily extended to include new deal types.
- All input/output to the application is by means of text files which can be easily edited.
- The software is modular and consists of a main C# program which calls both a compiled C# DealLibrary and also a compiled Analytics_MathLib. It should be mentioned that in many cases the C# deal class uses reasonable values for various parameters. For example, the number of time steps in a binomial lattice is set internally and cannot be altered by the user. The also initial random seed for Monte Carlo simulation is set internally to the same number (111) and this cannot be changed by the user.

We will now provide a brief overview of each component part of the application; more detail will be given later when specific deal classes are described.

# ## 8.1.1 The C# code

The application is defined by the C# solution PortfolioValuer.sln, and the projects DealLibrary.csproj and PortfolioValuer.csproj.