
*   `swapViewRefresh` will trigger a `useEffect` to refresh the list of swaps to show to the user. This is called when a change is made to a swap such as opening, updating, or closing a swap.

## Header and Footer

The Header and Footer components are included in the `components/layout.tsx` file and contain static information only.

## Wallet Connector

The wallet connector is a key component and contains the logic to connect to the `walletAPI` object and saves the wallet information to a `useState` variable in `pages/index.tsx`. The `walletAPI` and `walletInfo` variables are made available to all other components by passing them as props to every child and sub-child component. We build upon the same code and logic for connecting to a user wallet as discussed in *Chapter 5, Transaction Builder*. To improve the user experience, a list of installed and supported browser wallets is presented to the user to select from, as shown in *Figure 10.4*.

![](images/Figure-10.4.jpg)

**Figure 10.4:** Get Available Wallets[²](#c10.xhtml#ftn2)

There also exists a Wallet Connect[³](#c10.xhtml#ftn3) component created by the Cardano Foundation. However, due to overlap and duplication with the off-chain transaction builder frameworks, we will not be using it.

## Swap View

The swap view component obtains a list of swaps by calling `getFilterSwaps()` on line 43 in *Figure 10.5*. Filters will only be applied if they are set by the user using the `Filter` Button on the Get Tickets tab. SWR[⁴](#c10.xhtml#ftn4) is used to cache the list of Swaps unless the `getFilterSwaps()` returns a different result.

![](images/Figure-10.5.jpg)

**Figure 10.5:** Get FilterSwaps[⁵](#c10.xhtml#ftn5)

The array of swaps returned populates each swap card and paginates the view if necessary. Filter parameters are defined as state variables in the `SwapView` component and applied to the database query. The list of filter parameters is shown in *Figure 10.6*.

![](images/Figure-10.6.jpg)

**Figure 10.6:** Filter Parameters[⁶](#c10.xhtml#ftn6)

The API call to `pages/api/getFilterSwaps.ts` first creates a record object of the key/value filter parameters, as shown in *Figure 10.7*.

![](images/Figure-10.7.jpg)

**Figure 10.7:** getFilterSwaps API[⁷](#c10.xhtml#ftn7)

The record object is then passed to the `dynamicQuery()` function in *Figure 10.8*, which dynamically constructs the Redis database query and returns a filtered list of swaps.

![](images/Figure-10.8.jpg)

**Figure 10.8:** Redis Database Dynamic Query[⁸](#c10.xhtml#ftn8)

## Swap Card

Each Swap Card is passed the `swap`, `walletAPI`, `walletInfo`, and `setSwapViewRefresh` as props, as shown in *Figure 10.9*. These variables and functions display the Swap Card and are also passed to the `ExecuteSwap`, `UpdateSwap`, or `Close` `Swap` popup windows to build and submit a transaction.

![](images/Figure-10.9.jpg)

**Figure 10.9:** SwapCardProps Interface[⁹](#c10.xhtml#ftn9)

To execute a swap, a user selects the “`Buy`” button that changes the `buySwapOpen` variable to true. When this occurs, the `ExecuteSwapPopup` page component is shown to the user (see *Figure 10.10*).

![](images/Figure-10.10.jpg)

**Figure 10.10:** Execute Swap Popup Component[^(10)](#c10.xhtml#ftn10)

## Event View

The layout of the event page is similar to the swap view but requires the user to connect their wallet. Each event is linked to the wallet’s stake key, so we must connect the wallet first before creating a new event or seeing events already created.

## Event Card

The Event View contains Event Cards for each event linked to the connected wallet. The user can either sell tickets or archive the event. It also displays event statistics, such as the number of tickets allocated, released, and converted. All of this information is available on the blockchain, but we also update the database directly to provide faster, real-time updates within the application.

## My Tickets

On the `My Tickets` screen, the user is able to see the tickets that they currently have in their browser wallet with relevant metadata information such as event image, name, location, and showtime. This is also where the user can print each ticket and view the verification QR code, as shown in *Figure 10.11*. The NFT event tickets are Cardano native tokens, so they can also be viewed directly within the wallet or transferred to any other wallet or dApp, just like Ada.

![](images/Figure-10.11.jpg)

**Figure 10.11:** My Tickets View

## Print Tickets

When the `Print Ticket` Button is selected, a `Print Ticket` popup window will appear and allow the user to generate the QR code. Once the transaction is signed and the reference ticket CIP-68 metadata is updated, the QR code will be displayed. The signing of the transaction proves that they control the private key corresponding to the public key that the ticket asset is locked at. When the QR code is presented to the venue, the unique ticket will be marked used in the application DB to prevent double-redeeming of the ticket.

The `Verify` Button in *Figure 10.11* can be used to simulate a ticket redemption and granting access to an event. The QR code can be generated and saved in advance, which avoids having the user bring their wallet to the event venue and submitting a blockchain transaction at the time of entry. If the event ticket token is subsequently transferred to another person, the reference token datum history should be checked to confirm that it has not already been printed (or redeemed). The QR code is a string that includes the ticket asset name (minting policy hash + token name), the transaction hash, and the `witness signature` for the transaction that was signed and submitted, as shown in *Figure 10.12*.

![](images/Figure-10.12.jpg)

**Figure 10.12:** QR Code Generation[^(11)](#c10.xhtml#ftn11)

## Transaction Builder

The off-chain transaction builder code for swap operations such as open, update, execute, and close is done inside a popup window. When a popup window is enabled, a `useEffect` is triggered to call the appropriate function to build the off-chain transactions, as shown in *Figure 10.13*.

![](images/Figure-10.13.jpg)

**Figure 10.13:** Execute Swap useEffect[^(12)](#c10.xhtml#ftn12)

The off-chain code follows a similar pattern to the off-chain builder code in previous chapters. For an Execute Swap transaction, we will apply the contract parameters to build the Plutus script. If the swap validation is successful, we use the ticket minting policy to convert each ticket. Following the CIP-68 Metadata NFT standard, both the NFT token and the reference token are minted. On lines 224–227 in *Figure 10.14*, both the NFT tokens and the reference tokens are added to arrays that contain the total number of tokens to mint.

![](images/Figure-10.14.jpg)

**Figure 10.14:** Convert Tickets[^(13)](#c10.xhtml#ftn13)

During the swap transaction, we update the datum and create the outputs that will satisfy the business logic in the swap validator. This will ensure that the asking price and the amount of offered assets are correct. The `calcOrderDetails()` function determines the values that must be sent to the buyer and seller and returned to the swap, as shown in *Figure 10.15*.

![](images/Figure-10.15.jpg)

**Figure 10.15:** Calc Order Details[^(14)](#c10.xhtml#ftn14)
