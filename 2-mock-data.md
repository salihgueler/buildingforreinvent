Create TypeScript interfaces and mock data for a gaming marketplace:

1. User: id, username, email, avatar (dicebear URL), bio, joinDate, rating, totalTrades
2. Game: id, title, genre, platform, coverImage, description, releaseYear, metacriticScore
3. Listing: id, gameId, sellerId, condition (mint/excellent/good/fair/poor), price, createdAt
4. LibraryItem: userId, gameId, addedAt
5. Message: id, conversationId, senderId, content, timestamp, read
6. Conversation: id, participantIds[], lastMessage, lastMessageTime, unreadCount

Create mock data with:

- 3 users (gamer123, retrogamer, collector99)
- 8 games across different platforms (Switch, PS5, Xbox, PC)
- 4 marketplace listings
- 2 conversations with sample messages
- A currentMockUser variable that can be changed

Put this in src/data/mockData.ts

After creationg data:

Create a mock API in src/lib/mock-api.ts that simulates backend responses:

1. mockGamesApi: getAll, getById, create, update
2. mockListingsApi: getAll (with sellerId filter), getById, create, update, delete
3. mockUsersApi: getProfile (returns user with gameCollection, favoriteGames, tradingHistory, stats), getById, update
4. mockMessagesApi: getByConversation, send
5. mockConversationsApi: getAll, getOrCreate
6. mockLibraryApi: getByUserId, addGame, removeGame
7. mockAiChatApi: sendMessage (returns contextual responses based on keywords like "recommend", "trading", "deal", "condition")
8. mockAuth: login, signup, logout, setAuthenticated, getToken, setToken

Include:

- Simulated network delay (300ms)
- Authentication state tracking
- requireAuth() helper that throws if not authenticated
- Enrich responses with related data (e.g., listings include game and seller info)

After creating mock API:

Create src/lib/api-client.ts that wraps the mock API client:

1. Export an initializeApiClient function that accepts ApiConfig (apiEndpoint, region, userPoolId, userPoolClientId)
2. Export aiChat function for AI assistant
3. Export API objects: gamesApi, listingsApi, usersApi, messagesApi, conversationsApi, libraryApi

Each API object should delegate to the mock implementation.

Include commented-out code showing how to switch to a real AWS backend with:

- fetch-based apiCall function
- Authorization header with Bearer token
- Error handling for 401 responses
